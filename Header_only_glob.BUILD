# Library headers
HDRS = glob(["include/**/*.hpp", "include/**/*.h", "include/**/*.inl"])

# Public headers for library (strip containing include folder)
cc_library(
    name = "headers",
    hdrs = HDRS,
    strip_include_prefix = "include",
    visibility = ["//visibility:public"]
)