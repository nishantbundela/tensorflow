# Tests of TensorFlow linalg kernels written using the Python API.

load("//tensorflow:tensorflow.default.bzl", "cuda_py_strict_test", "tf_py_strict_test")

package(
    # copybara:uncomment default_applicable_licenses = ["//tensorflow:license"],
    licenses = ["notice"],
)

cuda_py_strict_test(
    name = "cholesky_op_test",
    size = "medium",
    srcs = ["cholesky_op_test.py"],
    shard_count = 5,
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:control_flow_ops",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:gradient_checker_v2",
        "//tensorflow/python:linalg_ops",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:stateless_random_ops",
        "//tensorflow/python:variables",
        "//tensorflow/python/client:session",
        "//tensorflow/python/framework:constant_op",
        "//tensorflow/python/framework:errors",
        "//tensorflow/python/framework:test_lib",
        "//tensorflow/python/ops/linalg",
        "//tensorflow/python/platform:benchmark",
        "//third_party/py/numpy",
    ],
)

cuda_py_strict_test(
    name = "determinant_op_test",
    size = "medium",
    srcs = ["determinant_op_test.py"],
    deps = [
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:control_flow_ops",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:linalg_ops",
        "//tensorflow/python:linalg_ops_gen",
        "//tensorflow/python:random_ops",
        "//tensorflow/python:variables",
        "//tensorflow/python/client:session",
        "//tensorflow/python/framework:constant_op",
        "//tensorflow/python/framework:test_lib",
        "//tensorflow/python/platform:benchmark",
        "//third_party/py/numpy",
    ],
)

tf_py_strict_test(
    name = "eig_op_test",
    size = "medium",
    srcs = ["eig_op_test.py"],
    data = ["//tensorflow/python/kernel_tests/linalg/testdata:self_adjoint_eig_op_test_files"],
    shard_count = 20,
    tags = [
        "no_windows",
        "nomsan",  # TODO(b/213581489): MSAN false positives from LAPACK use inside NumPy.
    ],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:gradient_checker_v2",
        "//tensorflow/python:linalg_ops",
        "//tensorflow/python:linalg_ops_gen",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:random_ops",
        "//tensorflow/python:sort_ops",
        "//tensorflow/python/framework:constant_op",
        "//tensorflow/python/framework:errors",
        "//tensorflow/python/framework:test_lib",
        "//third_party/py/numpy",
    ],
    # b/127344411: xla_enable_strict_auto_jit = True,
)

cuda_py_strict_test(
    name = "einsum_op_test",
    size = "medium",
    srcs = ["einsum_op_test.py"],
    shard_count = 4,
    xla_tags = [
        "no_cuda_asan",  # times out
    ],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:gradient_checker_v2",
        "//tensorflow/python:linalg_ops_gen",
        "//tensorflow/python:special_math_ops",
        "//tensorflow/python:variables",
        "//tensorflow/python/client:session",
        "//tensorflow/python/framework:constant_op",
        "//tensorflow/python/framework:errors",
        "//tensorflow/python/framework:test_lib",
        "//tensorflow/python/platform:benchmark",
        "//third_party/py/numpy",
    ],
)

cuda_py_strict_test(
    name = "linalg_grad_test",
    size = "medium",
    srcs = ["linalg_grad_test.py"],
    shard_count = 20,
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:gradient_checker_v2",
        "//tensorflow/python:gradients_impl",
        "//tensorflow/python:linalg_ops",
        "//tensorflow/python:math_ops",
        "//tensorflow/python/framework:constant_op",
        "//tensorflow/python/framework:test_lib",
        "//tensorflow/python/ops/linalg:linalg_impl",
        "//third_party/py/numpy",
    ],
)

cuda_py_strict_test(
    name = "linalg_ops_test",
    size = "medium",
    srcs = ["linalg_ops_test.py"],
    shard_count = 8,
    tags = ["no_windows_gpu"],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:linalg_ops",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:random_ops",
        "//tensorflow/python/framework:constant_op",
        "//tensorflow/python/framework:test_lib",
        "//tensorflow/python/ops/linalg",
        "//third_party/py/numpy",
        "@absl_py//absl/testing:parameterized",
    ],
)

cuda_py_strict_test(
    name = "linear_operator_addition_test",
    size = "small",
    srcs = ["linear_operator_addition_test.py"],
    deps = [
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:linalg_ops",
        "//tensorflow/python/ops/linalg",
        "//tensorflow/python/ops/linalg:linear_operator_addition",
        "//third_party/py/numpy",
    ],
)

cuda_py_strict_test(
    name = "linear_operator_adjoint_test",
    size = "medium",
    srcs = ["linear_operator_adjoint_test.py"],
    shard_count = 5,
    tags = [
        "optonly",  # times out
    ],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:variables",
        "//tensorflow/python/framework:config",
        "//tensorflow/python/ops/linalg",
        "//tensorflow/python/ops/linalg:linear_operator_adjoint",
        "//tensorflow/python/ops/linalg:linear_operator_test_util",
        "//third_party/py/numpy",
    ],
)

cuda_py_strict_test(
    name = "linear_operator_algebra_test",
    size = "small",
    srcs = ["linear_operator_algebra_test.py"],
    deps = [
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python/ops/linalg:cholesky_registrations",
        "//tensorflow/python/ops/linalg:linear_operator",
        "//tensorflow/python/ops/linalg:linear_operator_algebra",
        "//tensorflow/python/ops/linalg:matmul_registrations",
        "//tensorflow/python/ops/linalg:solve_registrations",
    ],
)

cuda_py_strict_test(
    name = "linear_operator_block_diag_test",
    size = "medium",
    srcs = ["linear_operator_block_diag_test.py"],
    shard_count = 8,
    tags = ["optonly"],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:variables",
        "//tensorflow/python/eager:context",
        "//tensorflow/python/framework:config",
        "//tensorflow/python/ops/linalg",
        "//tensorflow/python/ops/linalg:linear_operator_block_diag",
        "//tensorflow/python/ops/linalg:linear_operator_lower_triangular",
        "//tensorflow/python/ops/linalg:linear_operator_test_util",
        "//tensorflow/python/ops/linalg:linear_operator_util",
        "//third_party/py/numpy",
    ],
)

cuda_py_strict_test(
    name = "linear_operator_block_lower_triangular_test",
    size = "medium",
    srcs = ["linear_operator_block_lower_triangular_test.py"],
    shard_count = 8,
    tags = ["optonly"],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:variables",
        "//tensorflow/python/eager:backprop",
        "//tensorflow/python/eager:context",
        "//tensorflow/python/framework:config",
        "//tensorflow/python/ops/linalg",
        "//tensorflow/python/ops/linalg:linear_operator_block_lower_triangular",
        "//tensorflow/python/ops/linalg:linear_operator_test_util",
        "//tensorflow/python/ops/linalg:linear_operator_util",
        "//third_party/py/numpy",
    ],
)

cuda_py_strict_test(
    name = "linear_operator_composition_test",
    size = "medium",
    srcs = ["linear_operator_composition_test.py"],
    shard_count = 5,
    tags = [
        "optonly",  # times out
    ],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:math_ops",
        "//tensorflow/python/framework:config",
        "//tensorflow/python/ops/linalg",
        "//tensorflow/python/ops/linalg:linear_operator_test_util",
        "//third_party/py/numpy",
    ],
)

cuda_py_strict_test(
    name = "linear_operator_circulant_test",
    size = "medium",
    srcs = ["linear_operator_circulant_test.py"],
    shard_count = 15,
    tags = [
        "no_cuda11",  # TODO(b/197522782): reenable test after fixing.
        "optonly",  # times out, b/79171797
    ],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:array_ops_stack",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:variables",
        "//tensorflow/python/framework:config",
        "//tensorflow/python/ops/linalg",
        "//tensorflow/python/ops/linalg:linear_operator_circulant",
        "//tensorflow/python/ops/linalg:linear_operator_test_util",
        "//tensorflow/python/ops/signal:fft_ops",
        "//third_party/py/numpy",
        "@absl_py//absl/testing:parameterized",
    ],
)

cuda_py_strict_test(
    name = "linear_operator_diag_test",
    size = "medium",
    srcs = ["linear_operator_diag_test.py"],
    shard_count = 5,
    tags = ["optonly"],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:linalg_ops",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:random_ops",
        "//tensorflow/python:variables",
        "//tensorflow/python/framework:config",
        "//tensorflow/python/ops/linalg",
        "//tensorflow/python/ops/linalg:linear_operator_test_util",
    ],
)

cuda_py_strict_test(
    name = "linear_operator_full_matrix_test",
    size = "medium",
    srcs = ["linear_operator_full_matrix_test.py"],
    shard_count = 5,
    tags = ["optonly"],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:variables",
        "//tensorflow/python/framework:config",
        "//tensorflow/python/framework:errors",
        "//tensorflow/python/ops/linalg",
        "//tensorflow/python/ops/linalg:linear_operator_test_util",
    ],
)

cuda_py_strict_test(
    name = "linear_operator_householder_test",
    size = "medium",
    srcs = ["linear_operator_householder_test.py"],
    shard_count = 5,
    tags = ["optonly"],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:linalg_ops",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:variables",
        "//tensorflow/python/framework:config",
        "//tensorflow/python/ops/linalg",
        "//tensorflow/python/ops/linalg:linear_operator_householder",
        "//tensorflow/python/ops/linalg:linear_operator_test_util",
    ],
)

cuda_py_strict_test(
    name = "linear_operator_identity_test",
    size = "medium",
    srcs = ["linear_operator_identity_test.py"],
    shard_count = 5,
    tags = ["optonly"],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:linalg_ops",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:random_ops",
        "//tensorflow/python:variables",
        "//tensorflow/python/framework:config",
        "//tensorflow/python/framework:dtypes",
        "//tensorflow/python/ops/linalg",
        "//tensorflow/python/ops/linalg:linear_operator_test_util",
    ],
)

cuda_py_strict_test(
    name = "linear_operator_inversion_test",
    size = "medium",
    srcs = ["linear_operator_inversion_test.py"],
    shard_count = 5,
    tags = [
        "optonly",  # times out
    ],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:variables",
        "//tensorflow/python/framework:config",
        "//tensorflow/python/ops/linalg",
        "//tensorflow/python/ops/linalg:linear_operator_inversion",
        "//tensorflow/python/ops/linalg:linear_operator_test_util",
    ],
)

cuda_py_strict_test(
    name = "linear_operator_kronecker_test",
    size = "medium",
    srcs = ["linear_operator_kronecker_test.py"],
    shard_count = 10,
    tags = [
        "no_oss",  # TODO(b/282984925)
        "optonly",
    ],
    xla_enable_strict_auto_jit = True,
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:variables",
        "//tensorflow/python/framework:config",
        "//tensorflow/python/ops/linalg",
        "//tensorflow/python/ops/linalg:linear_operator_kronecker",
        "//tensorflow/python/ops/linalg:linear_operator_lower_triangular",
        "//tensorflow/python/ops/linalg:linear_operator_test_util",
        "//tensorflow/python/ops/linalg:linear_operator_util",
        "//third_party/py/numpy",
    ],
)

cuda_py_strict_test(
    name = "linear_operator_low_rank_update_test",
    size = "medium",
    srcs = ["linear_operator_low_rank_update_test.py"],
    shard_count = 10,
    tags = ["optonly"],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:variables",
        "//tensorflow/python/framework:config",
        "//tensorflow/python/ops/linalg",
        "//tensorflow/python/ops/linalg:linear_operator_test_util",
    ],
)

cuda_py_strict_test(
    name = "linear_operator_lower_triangular_test",
    size = "medium",
    srcs = ["linear_operator_lower_triangular_test.py"],
    shard_count = 4,
    tags = ["optonly"],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:variables",
        "//tensorflow/python/framework:config",
        "//tensorflow/python/ops/linalg",
        "//tensorflow/python/ops/linalg:linear_operator_test_util",
    ],
)

cuda_py_strict_test(
    name = "linear_operator_permutation_test",
    size = "medium",
    srcs = ["linear_operator_permutation_test.py"],
    shard_count = 5,
    tags = ["optonly"],
    xla_enable_strict_auto_jit = True,
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:linalg_ops",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:random_ops",
        "//tensorflow/python/framework:config",
        "//tensorflow/python/framework:constant_op",
        "//tensorflow/python/framework:dtypes",
        "//tensorflow/python/ops/linalg",
        "//tensorflow/python/ops/linalg:linear_operator_permutation",
        "//tensorflow/python/ops/linalg:linear_operator_test_util",
    ],
)

cuda_py_strict_test(
    name = "linear_operator_test",
    size = "small",
    srcs = ["linear_operator_test.py"],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:linalg_ops",
        "//tensorflow/python:math_ops",
        "//tensorflow/python/eager:context",
        "//tensorflow/python/framework:constant_op",
        "//tensorflow/python/ops/linalg",
        "//tensorflow/python/ops/parallel_for",
        "//third_party/py/numpy",
    ],
)

cuda_py_strict_test(
    name = "linear_operator_toeplitz_test",
    size = "medium",
    srcs = ["linear_operator_toeplitz_test.py"],
    shard_count = 5,
    tags = [
        "no_cuda_on_cpu_tap",  # flaky, b/135701551
        "no_gpu",  # flaky, b/135701551
        "optonly",  # times out, b/79171797
    ],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:variables",
        "//tensorflow/python/eager:backprop",
        "//tensorflow/python/ops/linalg",
        "//tensorflow/python/ops/linalg:linear_operator_test_util",
        "//tensorflow/python/ops/linalg:linear_operator_toeplitz",
        "//third_party/py/numpy",
    ],
)

cuda_py_strict_test(
    name = "linear_operator_tridiag_test",
    size = "medium",
    srcs = ["linear_operator_tridiag_test.py"],
    shard_count = 5,
    tags = [
        "no_windows_gpu",
        "optonly",
    ],
    xla_enable_strict_auto_jit = True,
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:array_ops_gen",
        "//tensorflow/python:array_ops_stack",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:manip_ops",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:variables",
        "//tensorflow/python/framework:config",
        "//tensorflow/python/ops/linalg",
        "//tensorflow/python/ops/linalg:linear_operator_test_util",
    ],
)

cuda_py_strict_test(
    name = "linear_operator_util_test",
    size = "medium",
    srcs = ["linear_operator_util_test.py"],
    shard_count = 5,
    tags = ["optonly"],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:linalg_ops",
        "//tensorflow/python:math_ops",
        "//tensorflow/python/ops/linalg",
        "//tensorflow/python/ops/linalg:linear_operator_util",
        "@absl_py//absl/testing:parameterized",
    ],
)

cuda_py_strict_test(
    name = "linear_operator_zeros_test",
    size = "medium",
    srcs = ["linear_operator_zeros_test.py"],
    shard_count = 5,
    tags = ["optonly"],  # Test is flaky without optimization.
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:variables",
        "//tensorflow/python/framework:dtypes",
        "//tensorflow/python/ops/linalg",
        "//tensorflow/python/ops/linalg:linear_operator_test_util",
    ],
)

cuda_py_strict_test(
    name = "lu_op_test",
    size = "small",
    srcs = ["lu_op_test.py"],
    xla_tags = [
        "no_cuda_asan",  # times out
    ],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:array_ops_stack",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:control_flow_ops",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:linalg_ops",
        "//tensorflow/python:map_fn",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:stateless_random_ops",
        "//tensorflow/python:variables",
        "//tensorflow/python/client:session",
        "//tensorflow/python/framework:errors",
        "//tensorflow/python/framework:test_lib",
        "//tensorflow/python/platform:benchmark",
        "//third_party/py/numpy",
    ],
)

tf_py_strict_test(
    name = "matrix_exponential_op_test",
    size = "medium",
    srcs = ["matrix_exponential_op_test.py"],
    shard_count = 16,
    tags = ["no_windows_gpu"],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:control_flow_ops",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:random_ops",
        "//tensorflow/python:variables",
        "//tensorflow/python/client:session",
        "//tensorflow/python/framework:constant_op",
        "//tensorflow/python/framework:test_lib",
        "//tensorflow/python/ops/linalg:linalg_impl",
        "//tensorflow/python/platform:benchmark",
        "//third_party/py/numpy",
    ],
)

cuda_py_strict_test(
    name = "matrix_inverse_op_test",
    size = "small",
    srcs = ["matrix_inverse_op_test.py"],
    tags = ["optonly"],
    deps = [
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:control_flow_ops",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:linalg_ops",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:random_ops",
        "//tensorflow/python:variables",
        "//tensorflow/python/client:session",
        "//tensorflow/python/framework:constant_op",
        "//tensorflow/python/framework:test_lib",
        "//tensorflow/python/platform:benchmark",
        "//third_party/py/numpy",
    ],
)

tf_py_strict_test(
    name = "matrix_logarithm_op_test",
    size = "medium",
    srcs = ["matrix_logarithm_op_test.py"],
    deps = [
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:control_flow_ops",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:linalg_ops_gen",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:stateless_random_ops",
        "//tensorflow/python:variables",
        "//tensorflow/python/client:session",
        "//tensorflow/python/framework:constant_op",
        "//tensorflow/python/framework:errors",
        "//tensorflow/python/framework:test_lib",
        "//tensorflow/python/ops/linalg:linalg_impl",
        "//tensorflow/python/platform:benchmark",
        "//third_party/py/numpy",
    ],
)

cuda_py_strict_test(
    name = "matrix_solve_ls_op_test",
    size = "medium",
    srcs = ["matrix_solve_ls_op_test.py"],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:control_flow_ops",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:linalg_ops",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:variables",
        "//tensorflow/python/client:session",
        "//tensorflow/python/eager:context",
        "//tensorflow/python/framework:constant_op",
        "//tensorflow/python/framework:errors",
        "//tensorflow/python/framework:test_lib",
        "//tensorflow/python/platform:benchmark",
        "//third_party/py/numpy",
    ],
)

cuda_py_strict_test(
    name = "matrix_solve_op_test",
    size = "medium",
    srcs = ["matrix_solve_op_test.py"],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:control_flow_ops",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:linalg_ops",
        "//tensorflow/python:stateless_random_ops",
        "//tensorflow/python:variables",
        "//tensorflow/python/client:session",
        "//tensorflow/python/eager:context",
        "//tensorflow/python/framework:constant_op",
        "//tensorflow/python/framework:errors",
        "//tensorflow/python/framework:test_lib",
        "//tensorflow/python/platform:benchmark",
        "//third_party/py/numpy",
    ],
)

cuda_py_strict_test(
    name = "matrix_square_root_op_test",
    size = "medium",
    srcs = ["matrix_square_root_op_test.py"],
    deps = [
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:linalg_ops_gen",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:stateless_random_ops",
        "//tensorflow/python/framework:constant_op",
        "//tensorflow/python/framework:errors",
        "//tensorflow/python/framework:test_lib",
        "//third_party/py/numpy",
    ],
)

cuda_py_strict_test(
    name = "matrix_triangular_solve_op_test",
    size = "medium",
    srcs = ["matrix_triangular_solve_op_test.py"],
    shard_count = 3,
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:linalg_ops",
        "//tensorflow/python/framework:test_lib",
        "//third_party/py/numpy",
    ],
)

cuda_py_strict_test(
    name = "normalize_op_test",
    size = "medium",
    srcs = ["normalize_op_test.py"],
    shard_count = 20,
    # TODO(b/117236102): Re-enable in msan build.
    tags = ["no_windows_gpu"],
    # TODO(b/208263392): Re-enable. tf.Squeeze op after tf.Where op doesn't reshape.
    xla_enable_strict_auto_jit = False,
    deps = [
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:nn",
        "//tensorflow/python/framework:test_lib",
        "//third_party/py/numpy",
    ],
)

cuda_py_strict_test(
    name = "norm_op_test",
    size = "medium",
    srcs = ["norm_op_test.py"],
    shard_count = 20,
    # TODO(b/117236102): Re-enable in msan build.
    tags = ["no_windows_gpu"],
    # TODO(b/208263392): Re-enable. tf.Squeeze op after tf.Where op doesn't reshape.
    xla_enable_strict_auto_jit = False,
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:linalg_ops",
        "//tensorflow/python/framework:constant_op",
        "//tensorflow/python/framework:test_lib",
        "//third_party/py/numpy",
    ],
)

cuda_py_strict_test(
    name = "qr_op_test",
    size = "medium",
    srcs = ["qr_op_test.py"],
    shard_count = 20,
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:control_flow_ops",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:gradient_checker_v2",
        "//tensorflow/python:linalg_ops",
        "//tensorflow/python:stateless_random_ops",
        "//tensorflow/python:variables",
        "//tensorflow/python/client:session",
        "//tensorflow/python/eager:backprop",
        "//tensorflow/python/eager:context",
        "//tensorflow/python/framework:constant_op",
        "//tensorflow/python/framework:errors",
        "//tensorflow/python/framework:test_lib",
        "//tensorflow/python/platform:benchmark",
        "//third_party/py/numpy",
    ],
)

cuda_py_strict_test(
    name = "self_adjoint_eig_op_test",
    size = "medium",
    srcs = ["self_adjoint_eig_op_test.py"],
    data = ["//tensorflow/python/kernel_tests/linalg/testdata:self_adjoint_eig_op_test_files"],
    shard_count = 20,
    tags = [
        "no_windows",
    ],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:gradient_checker_v2",
        "//tensorflow/python:linalg_ops",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:random_ops",
        "//tensorflow/python/framework:constant_op",
        "//tensorflow/python/framework:test_lib",
        "//third_party/py/numpy",
    ],
    # TODO(b/127344411): This test passes because XLA does not actually cluster
    # the self_adjoint_eig op.
)

cuda_py_strict_test(
    name = "slicing_test",
    size = "small",
    srcs = ["slicing_test.py"],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python/framework:constant_op",
        "//tensorflow/python/framework:errors",
        "//tensorflow/python/ops/linalg",
        "//tensorflow/python/ops/linalg:linear_operator_test_util",
        "//tensorflow/python/ops/linalg:slicing",
    ],
)

cuda_py_strict_test(
    name = "svd_op_test",
    size = "medium",
    srcs = ["svd_op_test.py"],
    shard_count = 30,
    tags = [
        "no_oss",  # b/117185141.
    ],
    xla_tags = [
        "no_cuda_asan",  # times out
    ],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:control_flow_ops",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:gradient_checker",
        "//tensorflow/python:gradient_checker_v2",
        "//tensorflow/python:gradients_impl",
        "//tensorflow/python:linalg_ops",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:stateless_random_ops",
        "//tensorflow/python:variables",
        "//tensorflow/python/client:session",
        "//tensorflow/python/eager:context",
        "//tensorflow/python/framework:constant_op",
        "//tensorflow/python/framework:errors",
        "//tensorflow/python/framework:test_lib",
        "//tensorflow/python/platform:benchmark",
        "//third_party/py/numpy",
    ],
    # TODO(b/127344411): This test passes because XLA does not actually cluster
    # the svd op.
)

cuda_py_strict_test(
    name = "tridiagonal_matmul_op_test",
    size = "medium",
    srcs = ["tridiagonal_matmul_op_test.py"],
    shard_count = 10,
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:array_ops_stack",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:control_flow_ops",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:gradient_checker_v2",
        "//tensorflow/python:linalg_ops",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:variables",
        "//tensorflow/python/client:session",
        "//tensorflow/python/eager:context",
        "//tensorflow/python/framework:constant_op",
        "//tensorflow/python/framework:errors",
        "//tensorflow/python/ops/linalg:linalg_impl",
        "//tensorflow/python/platform:benchmark",
        "//third_party/py/numpy",
    ],
)

cuda_py_strict_test(
    name = "tridiagonal_solve_op_test",
    size = "medium",
    srcs = ["tridiagonal_solve_op_test.py"],
    shard_count = 12,
    tags = [
        "no_oss",  # TODO(b/142818120): Re-enable.
    ],
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:control_flow_ops",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:variables",
        "//tensorflow/python/client:session",
        "//tensorflow/python/eager:backprop",
        "//tensorflow/python/eager:context",
        "//tensorflow/python/framework:constant_op",
        "//tensorflow/python/framework:test_lib",
        "//tensorflow/python/ops/linalg:linalg_impl",
        "//tensorflow/python/platform:benchmark",
        "//third_party/py/numpy",
    ],
)
