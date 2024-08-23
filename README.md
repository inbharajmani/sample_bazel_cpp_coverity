## Introduction

This is a sample C++ project uses bazel build system.

## Prerequisites
- To build this example project install bazel using official docs [here](https://bazel.build/install).
- Coverity analysis version 2023.6.0
- Modify rules_coverity.tar.gz [absolute path](https://github.com/inbharajmani/sample_bazel_cpp_coverity/blob/14304ec5553982478d8c4e4d255c6da2c8ee8109/WORKSPACE#L4) according to your cov-analysis installed with having rules_coverity.tar.gz(otherwise coverity build will fail)

## Native Build
```
bazel build //main:hello-world
```

If the build is successful, Bazel prints the output similar to
```
____Loading complete.  Analyzing...
____Found 1 target...
____Building...
Target //main:hello-world up-to-date:
  C:/tools/msys64/tmp/_bazel_woden/vqeu6v3v/execroot/__main__/bazel-out/msvc_x64-fastbuild/bin/main/hello-world.exe
____Elapsed time: 0,400s, Critical Path: 0,01s
```
## Clean

```
bazel clean --expunge
```
## Coverity cmd line build steps

- Cov-configure

```
cov-configure --config coverity/coverity_config.xml --gcc 
```

- Cov-build

```
cov-build --emit-complementary-info --config coverity/coverity_config.xml --dir coverity --bazel bazel build //main:coverity_build
```
- Cov-analyze

```
cov-analyze --dir coverity/ --all --verbose 2 --strip-path $(bazel info execution_root)
```

- Cov-commit

```
cov-commit-defects --dir coverity/ --stream local_coverity --url **url** --user **username** --password **password**
```

## Violation

- If Coverity succeds it will capture the deadcode present [at this line](https://github.com/inbharajmani/sample_bazel_cpp_coverity/blob/14304ec5553982478d8c4e4d255c6da2c8ee8109/main/hello-world.cc#L20)