# How to use this repository

- clone the repository.
- install bazel [bazel](https://github.com/bazelbuild/bazel) or [bazelisk](https://github.com/bazelbuild/bazelisk) or use `./bazelisk.sh` .
- run `bazel build example:hello-world` to build `example/main.cc` targets.
  - if you are using `./bazelisk.sh` , then run `./bazelisk.sh build example:hello-world`. 
- check the output in `bazel-bin/example/hello_world`.
- build **hex file**: `bazel build example:hello_world.hex`
- build **bin file**: `bazel build example:hello_world.bin`

```log
INFO: Invocation ID: 1f20e7d2-906c-4b20-9775-2cbb728d0bfa
INFO: Analyzed target //example:hello_world (74 packages loaded, 6260 targets configured).
INFO: Found 1 target...
Target //example:hello_world up-to-date:
  bazel-bin/example/hello_world
INFO: Elapsed time: 0.417s, Critical Path: 0.01s
INFO: 2 processes: 5 action cache hit, 2 internal.
INFO: Build completed successfully, 2 total actions
```


# Toolchain Configuration

configure toolchains for building xpack targets
[BUILD](toolchains/toolchains/xpack-riscv-none-elf-gcc/BUILD)