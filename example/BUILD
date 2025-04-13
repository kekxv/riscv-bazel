# BUILD (in root directory)

cc_binary(
    name = "hello_world",
    srcs = ["main.cc"],
    # No toolchain specified here - relies on registration and auto-detection
)

genrule(
    name = "hello_world.hex",
    srcs = [":hello_world"],
    outs = ["hello_world.hex"],
    cmd = "$(OBJCOPY) -Oihex $(location :hello_world) $(@)",
    toolchains = ["@bazel_tools//tools/cpp:current_cc_toolchain"],
)

genrule(
    name = "hello_world.bin",
    srcs = [":hello_world"],
    outs = ["hello_world.bin"],
    cmd = "$(OBJCOPY) -Obinary $(location :hello_world) $(@)",
    toolchains = ["@bazel_tools//tools/cpp:current_cc_toolchain"],
)
