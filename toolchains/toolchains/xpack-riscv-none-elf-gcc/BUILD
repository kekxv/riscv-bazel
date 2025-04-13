# Load the new macro
load("//toolchains/toolchains:cc_mini_toolchain.bzl", "cc_mini_toolchain")

filegroup(
    name = "wrappers",
    srcs = glob(["wrappers/**"]),
)

filegroup(
    name = "toolchain_all_files",  # Renamed for clarity
    srcs = [
        ":wrappers",
        "@xpack-riscv-none-elf-gcc-linux-x64//:toolchain",  # Assuming this provides headers/libs/sysroot components
    ],
)

cc_mini_toolchain(
    # Base name for the toolchain rules (toolchain, cc_toolchain, config)
    name = "toolchains",  # Choose a descriptive name
    # --- File Dependencies ---
    all_files = ":toolchain_all_files",
    compiler = "gcc",  # Assuming wrappers ultimately call gcc
    # sysroot = "external/glibc-linux-gnu-x86_64/x86_64-buildroot-linux-gnu/sysroot", # Example if needed

    # --- Flags (Extracted from your original features) ---
    compiler_flags = [
        "-no-canonical-prefixes",
        "-fno-canonical-system-headers",
        # "-Wno-builtin-macro-redefined",
        # "-D__DATE__=\"redacted\"",
        # "-D__TIMESTAMP__=\"redacted\"",
        # "-D__TIME__=\"redacted\"",
        # "-fPIC",
        "-march=rv32imafc",
        "-mabi=ilp32f",
        "-msmall-data-limit=8",
        "-mno-save-restore",
        "-Os",
        "-fmessage-length=0",
        "-fsigned-char",
        "-ffunction-sections",
        "-fdata-sections",
        "-Wunused",
        "-Wuninitialized",
        "-MMD",
        "-MP",
    ],
    cpp_flags = [
        # C++ specific flags (will be appended to compiler_flags for C++ actions)
        "-std=c++17",
        "-march=rv32imafc",
        "-mabi=ilp32f",
        "-msmall-data-limit=8",
        "-mno-save-restore",
        "-Os",
        "-fmessage-length=0",
        "-fsigned-char",
        "-ffunction-sections",
        "-fdata-sections",
        "-Wunused",
        "-Wuninitialized",
        #"-std=gnu99",
        "-MMD",
        "-MP",
    ],
    dynamic_library_linking_flags = [
        "-shared",
        "-march=rv32imafc",
        "-mabi=ilp32f",
        "-msmall-data-limit=8",
        "-mno-save-restore",
        "-Os",
        "-fmessage-length=0",
        "-fsigned-char",
        "-ffunction-sections",
        "-fdata-sections",
        "-Wunused",
        "-Wuninitialized",
    ],
    executable_linking_flags = [
        "-static",
        "-march=rv32imafc",
        "-mabi=ilp32f",
        "-msmall-data-limit=8",
        "-mno-save-restore",
        "-Os",
        "-fmessage-length=0",
        "-fsigned-char",
        "-ffunction-sections",
        "-fdata-sections",
        "-Wunused",
        "-Wuninitialized",
    ],
    linker_flags = [
        "-lstdc++",
        "-march=rv32imafc",
        "-mabi=ilp32f",
        "-msmall-data-limit=8",
        "-mno-save-restore",
        "-Os",
        "-fmessage-length=0",
        "-fsigned-char",
        "-ffunction-sections",
        "-fdata-sections",
        "-Wunused",
        "-Wuninitialized",
        #"--specs=nano.specs",
        #"--specs=nosys.specs",
        #"-nostartfiles",
        "-Xlinker",
        "--gc-sections",
    ],
    platform = {
        "host_cpu": "x86_64",
        "host_os": "linux",
        "target_cpu": "riscv32",  # Adjusted to a more standard Bazel CPU value
        "target_os": "linux",
    },
    supports_pic = True,  # Based on your -fPIC flag
    target_libc = "glibc",  # Be more specific if known, else keep "unknown"

    # --- Tool Paths (Relative to this package) ---
    tool_paths_dict = {
        "gcc": "wrappers/gcc",
        "ld": "wrappers/ld",
        "cpp": "wrappers/g++",  # Often same as gcc, but separate entry is fine
        "ranlib": "wrappers/ranlib",
        "nm": "wrappers/nm",
        "objdump": "wrappers/objdump",
        "objcopy": "wrappers/objcopy",
        "ar": "wrappers/ar",
        "strip": "wrappers/strip",
        # Add "gcov" or other toolchains if needed
    },

    # Pass visibility if needed for the final 'toolchain' rule
    visibility = ["//visibility:public"],
)
