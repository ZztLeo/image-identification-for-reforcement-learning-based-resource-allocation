# Headers for 2D Fast Fourier Transform package
# from http://momonga.t.u-tokyo.ac.jp/~ooura/fft.html
# This is a separate package because the original downloaded archive doesn't
# contain any header files.

package(
    default_visibility = ["//visibility:public"],
)

# Unrestricted use; can only distribute original package.
# See fft/readme.txt
licenses(["notice"])

exports_files(["LICENSE"])

cc_library(
    name = "fft2d_headers",
    srcs = ["fft.h"],
)

objc_library(
    name = "fft2d_headersd_ios",
    srcs = ["fft.h"],
)

# Export the source code so that it could be compiled for Andoid native apps.
filegroup(
    name = "fft2d_headers_srcs",
    srcs = ["fft.h"],
)

filegroup(
    name = "all_files",
    srcs = glob(
        ["**/*"],
        exclude = ["**/OWNERS"],
    ),
    visibility = ["//tensorflow:__subpackages__"],
)
