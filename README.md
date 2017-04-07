We found an issue while using `bazel-0.4.5` on OSX. This repository is a minimal setup which helps reproduce/debug the problem.

Symptom
-------

Bazel does not detect changes in `.h` file.

Steps to reproduce
------------------

```
brew install bazel # make sure you have bazel-0.4.5 installed.

# Clone this repo.
git clone https://github.com/soonho-tri/bazel_0.4.5_osx_bug.git
cd bazel_0.4.5_osx_bug

# First build.
bazel build --crosstool_top=//tools:default-toolchain :helloworld

# Insert "abcde" at the first line of main.h
# This should causes a compilation error.

# Second build.
bazel build --crosstool_top=//tools:default-toolchain :helloworld

# BUG: the above line does *NOT* generate a compilation error:
# INFO: Found 11 targets...
# INFO: Elapsed time: 0.167s, Critical Path: 0.00s
```

Remarks
-------

Bazel Version | Ubuntu  | OSX
------------- | ------- | ----
0.4.4         |   OK    |  OK
0.4.5         |   OK    |  Bug (fine without using `--crosstool_top` option)

