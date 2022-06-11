# Self-contained bazel file for use of pre-compiled libraries.
# Can be put in library root and changed as needed.
# Currently designed for within WORKSPACE builds.

# Example below is for SDL2 (https://www.libsdl.org/)
# A dynamic shared library that requires a DLL at runtime.

# Library headers
HDRS = glob(["include/*.h"])

# Static library files for each platform
LIB = select({
    "@bazel_tools//src/conditions:windows_x64" : ["lib/x64/SDL2.lib", "lib/x64/SDL2main.lib"],
    "//conditions:default" : []
})

# Specifc link options for each platform
LINK_OPTS = select({
    "@bazel_tools//src/conditions:windows_x64" : ["shell32.lib"],
    "//conditions:default" : []
})

# Public headers for library (strip containing include folder)
cc_library(
    name = "headers",
    hdrs = HDRS,
    strip_include_prefix = "include",
    visibility = ["//visibility:public"]
)

# Library to link against
# The sub select is for locating required dynamically loaded libraries (can be removed if not required)
cc_library(
    name = "lib",
    srcs = LIB,
    linkopts = LINK_OPTS,
    deps = [
        ":headers",
    ] + select({
        "@bazel_tools//src/conditions:windows_x64" : [":windows_x64"]
    }),
    visibility = ["//visibility:public"]
)

# Declare a dynamic library for a platform so Bazel will move it to correct locations
cc_import(
    name = "windows_x64",
    shared_library = "lib/x64/SDL2.dll"
)