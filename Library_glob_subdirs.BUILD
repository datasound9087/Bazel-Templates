# Library headers
HDRS = glob(["include/**/*.h"])
SRCS = glob(["src/**/.cpp"])

# Public headers for library (strip containing include folder)
cc_library(
    name = "headers",
    hdrs = HDRS,
    strip_include_prefix = "include",
    visibility = ["//visibility:public"]
)

cc_library(
    name = "lib",
    hdrs = HDRS,
    srcs = SRCS,
    deps = [
        ":headers",
        "@rules_vulkan//vulkan:vulkan_cc_library",
    ],
    visibility = ["//visibility:public"]
)