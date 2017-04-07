Reproducible Steps

```
brew install bazel # make sure you have bazel-0.4.5 installed.

# First build.
bazel build --crosstool_top=//tools:default-toolchain :helloworld

# Insert "abcde" at the first line of main.h
# This should causes a compilation error.

# Second build.
bazel build --crosstool_top=//tools:default-toolchain :helloworld
```
