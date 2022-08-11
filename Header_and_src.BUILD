# Library headers
HDRS = glob(["include/*.h"])
SRCS = glob(["src/*.cpp"])

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
    srcs = SRCS,
    deps = [
        ":headers",
        "//ext/sdl2:headers"
    ],
    visibility = ["//visibility:public"]
)