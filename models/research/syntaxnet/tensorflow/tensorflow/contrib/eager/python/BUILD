licenses(["notice"])  # Apache 2.0

package(default_visibility = ["//tensorflow:internal"])

load("//tensorflow:tensorflow.bzl", "py_test")
load("//tensorflow:tensorflow.bzl", "cuda_py_test")

py_library(
    name = "tfe",
    srcs = ["tfe.py"],
    srcs_version = "PY2AND3",
    visibility = ["//visibility:public"],
    deps = [
        ":checkpointable_utils",
        ":datasets",
        ":metrics",
        ":network",
        ":saver",
        "//tensorflow/python:framework_ops",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:gradients",
        "//tensorflow/python:numerics",
        "//tensorflow/python:resource_variable_ops",
        "//tensorflow/python:script_ops",
        "//tensorflow/python:template",
        "//tensorflow/python:util",
        "//tensorflow/python:variable_scope",
        "//tensorflow/python/eager:backprop",
        "//tensorflow/python/eager:context",
        "//tensorflow/python/eager:core",
        "//tensorflow/python/eager:execution_callbacks",
        "//tensorflow/python/eager:function",
    ],
)

cuda_py_test(
    name = "tfe_test",
    srcs = ["tfe_test.py"],
    additional_deps = [
        ":tfe",
        "//tensorflow/python:array_ops",
        "//tensorflow/python:metrics",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:platform_test",
        "//tensorflow/python:summary",
    ],
)

py_library(
    name = "datasets",
    srcs = ["datasets.py"],
    srcs_version = "PY2AND3",
    visibility = ["//tensorflow:internal"],
    deps = [
        "//tensorflow/contrib/data/python/ops:prefetching_ops",
        "//tensorflow/python:array_ops",
        "//tensorflow/python:dataset_ops_gen",
        "//tensorflow/python:errors",
        "//tensorflow/python:framework_ops",
        "//tensorflow/python:resource_variable_ops",
        "//tensorflow/python/data/ops:iterator_ops",
        "//tensorflow/python/data/util:nest",
        "//tensorflow/python/eager:context",
    ],
)

cuda_py_test(
    name = "datasets_test",
    srcs = ["datasets_test.py"],
    additional_deps = [
        ":datasets",
        ":checkpointable_utils",
        "//tensorflow/contrib/data/python/ops:transformation_ops",
        "//tensorflow/contrib/lookup:lookup_py",
        "//tensorflow/python:dtypes",
        "//tensorflow/python:framework_ops",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:script_ops",
        "//tensorflow/python/data",
        "//tensorflow/python/eager:test",
    ],
    tags = ["noguitar"],
)

py_library(
    name = "saver",
    srcs = ["saver.py"],
    srcs_version = "PY2AND3",
    deps = [
        "//tensorflow/python:errors",
        "//tensorflow/python:framework_ops",
        "//tensorflow/python:resource_variable_ops",
        "//tensorflow/python:training",
        "//tensorflow/python/eager:context",
    ],
)

cuda_py_test(
    name = "saver_test",
    srcs = ["saver_test.py"],
    additional_deps = [
        ":saver",
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python/eager:graph_callable",
        "//tensorflow/python/eager:test",
        "//tensorflow/python:variables",
    ],
)

py_library(
    name = "metrics",
    srcs = [
        "metrics.py",
        "metrics_impl.py",
    ],
    srcs_version = "PY2AND3",
    visibility = ["//tensorflow:internal"],
    deps = [
        "//tensorflow/contrib/eager/python:checkpointable_utils",
        "//tensorflow/contrib/summary:summary_ops",
        "//tensorflow/python:array_ops",
        "//tensorflow/python:control_flow_ops",
        "//tensorflow/python:dtypes",
        "//tensorflow/python:framework_ops",
        "//tensorflow/python:init_ops",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:util",
        "//tensorflow/python:variable_scope",
        "//tensorflow/python/eager:context",
        "//tensorflow/python/eager:function",
    ],
)

py_test(
    name = "metrics_test",
    srcs = ["metrics_test.py"],
    srcs_version = "PY2AND3",
    deps = [
        ":metrics",
        "//tensorflow/contrib/summary:summary_ops",
        "//tensorflow/contrib/summary:summary_test_util",
        "//tensorflow/python:array_ops",
        "//tensorflow/python:dtypes",
        "//tensorflow/python:framework_ops",
        "//tensorflow/python:training",
        "//tensorflow/python/eager:context",
        "//tensorflow/python/eager:test",
    ],
)

py_library(
    name = "evaluator",
    srcs = [
        "evaluator.py",
    ],
    srcs_version = "PY2AND3",
    visibility = ["//tensorflow:internal"],
    deps = [
        ":datasets",
        ":metrics",
        "//tensorflow/contrib/summary:summary_ops",
        "//tensorflow/python:control_flow_ops",
        "//tensorflow/python:errors",
        "//tensorflow/python:framework_ops",
        "//tensorflow/python/eager:context",
        "//tensorflow/python/eager:function",
        "@six_archive//:six",
    ],
)

py_test(
    name = "evaluator_test",
    srcs = ["evaluator_test.py"],
    srcs_version = "PY2AND3",
    deps = [
        ":evaluator",
        ":metrics",
        "//tensorflow/contrib/summary:summary_test_util",
        "//tensorflow/python:framework_ops",
        "//tensorflow/python:training",
        "//tensorflow/python:variables",
        "//tensorflow/python/data/ops:dataset_ops",
        "//tensorflow/python/eager:context",
        "//tensorflow/python/eager:test",
    ],
)

py_library(
    name = "network",
    srcs = ["network.py"],
    srcs_version = "PY2AND3",
    visibility = ["//tensorflow:internal"],
    deps = [
        "//tensorflow/python:framework_ops",
        "//tensorflow/python:layers_base",
        "//tensorflow/python:training",
        "//tensorflow/python:variable_scope",
        "//tensorflow/python/eager:context",
        "//tensorflow/python/estimator:util",
    ],
)

py_test(
    name = "network_test",
    srcs = ["network_test.py"],
    srcs_version = "PY2AND3",
    deps = [
        ":network",
        "//tensorflow/contrib/layers:layers_py",
        "//tensorflow/python:constant_op",
        "//tensorflow/python:errors",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:layers",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:nn_ops",
        "//tensorflow/python:resource_variable_ops",
        "//tensorflow/python:training",
        "//tensorflow/python:variable_scope",
        "//tensorflow/python/eager:function",
        "//tensorflow/python/eager:test",
    ],
)

py_library(
    name = "checkpointable_utils",
    srcs = ["checkpointable_utils.py"],
    srcs_version = "PY2AND3",
    visibility = ["//tensorflow:internal"],
    deps = [
        "//tensorflow/contrib/eager/proto:checkpointable_object_graph_proto_py",
        "//tensorflow/python:constant_op",
        "//tensorflow/python:control_flow_ops",
        "//tensorflow/python:dtypes",
        "//tensorflow/python:errors",
        "//tensorflow/python:framework_ops",
        "//tensorflow/python:init_ops",
        "//tensorflow/python:pywrap_tensorflow",
        "//tensorflow/python:resource_variable_ops",
        "//tensorflow/python:session",
        "//tensorflow/python:tensor_shape",
        "//tensorflow/python:training",
        "//tensorflow/python:util",
        "//tensorflow/python:variable_scope",
        "//tensorflow/python/eager:context",
    ],
)

cuda_py_test(
    name = "checkpointable_utils_test",
    srcs = ["checkpointable_utils_test.py"],
    additional_deps = [
        ":checkpointable_utils",
        ":network",
        "@six_archive//:six",
        "//tensorflow/python:constant_op",
        "//tensorflow/python:dtypes",
        "//tensorflow/python:framework_ops",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:init_ops",
        "//tensorflow/python:layers",
        "//tensorflow/python:layers_base",
        "//tensorflow/python:resource_variable_ops",
        "//tensorflow/python:state_ops",
        "//tensorflow/python:training",
        "//tensorflow/python:variable_scope",
        "//tensorflow/python:variables",
        "//tensorflow/python/eager:context",
        "//tensorflow/python/eager:test",
        "//tensorflow/python/keras",
    ],
    tags = [
        "no_windows",  # TODO: needs investigation on Windows
        "notsan",  # b/74395663
    ],
)
