load("@rules_cc//cc:defs.bzl", "cc_binary")

cc_binary(
    name = "hello-world",
    srcs = ["hello-world.cc"]
)

load("@rules_coverity//coverity:defs.bzl", "cov_gen_script")

cov_gen_script(
    name="coverity_build",
    deps=[":hello-world"]
)