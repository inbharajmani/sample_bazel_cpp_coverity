load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
http_archive(
    name="rules_coverity",
    urls=["file:///home/inbmani/cov-analysis-linux64-2023.6.0/bazel/rules_coverity.tar.gz"]
)

load("@rules_coverity//coverity:repositories.bzl", "rules_coverity_toolchains")
rules_coverity_toolchains()
