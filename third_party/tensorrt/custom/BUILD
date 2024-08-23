load("@rules_cc//cc:defs.bzl", "cc_import", "cc_library")

package(default_visibility = ["//visibility:public"])

config_setting(
    name = "aarch64_linux",
    constraint_values = [
        "@platforms//cpu:aarch64",
        "@platforms//os:linux",
    ],
)

cc_library(
    name = "nvinfer_headers",
    hdrs = glob(["include/aarch64-linux-gnu/NvInfer*.h"]),
    includes = ["include/aarch64-linux-gnu"],
    visibility = ["//visibility:public"],
)

cc_import(
    name = "nvinfer_lib",
    shared_library = "lib/aarch64-linux-gnu/libnvinfer.so",
    visibility = ["//visibility:public"],
)

cc_library(
    name = "nvinfer",
    visibility = ["//visibility:public"],
    deps = [
        ":nvinfer_headers",
        ":nvinfer_lib",
    ],
)

cc_import(
    name = "nvparsers_lib",
    shared_library = "lib/aarch64-linux-gnu/libnvparsers.so",
    visibility = ["//visibility:public"],
)

cc_library(
    name = "nvparsers",
    visibility = ["//visibility:public"],
    deps = [
        ":nvinfer",
        ":nvparsers_lib",
    ],
)

cc_import(
    name = "nvonnxparser_lib",
    shared_library = "lib/aarch64-linux-gnu/libnvonnxparser.so",
    visibility = ["//visibility:public"],
)

cc_library(
    name = "nvonnxparser",
    visibility = ["//visibility:public"],
    deps = [
        ":nvinfer",
        ":nvonnxparser_lib",
    ],
)

cc_import(
    name = "nvinfer_plugin_lib",
    shared_library = "lib/aarch64-linux-gnu/libnvinfer_plugin.so",
    visibility = ["//visibility:public"],
)

cc_library(
    name = "nvinferplugin",
    visibility = ["//visibility:public"],
    deps = [
        ":nvinfer",
        ":nvinfer_plugin_lib",
    ],
    alwayslink = True,
)