workspace(name = "repro-gql")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

# https://github.com/bazelbuild/rules_nodejs/releases
http_archive(
    name = "build_bazel_rules_nodejs",
    sha256 = "4913ea835810c195df24d3a929315c29a64566cc48e409d8b0f35008b4e02e59",
    urls = ["https://github.com/bazelbuild/rules_nodejs/releases/download/4.4.4/rules_nodejs-4.4.4.tar.gz"],
)

load("@build_bazel_rules_nodejs//:index.bzl", "node_repositories", "yarn_install")

node_repositories(
    node_version = "16.11.0",
    # preserve_symlinks = False,
)

yarn_install(
    # Name this npm so that Bazel Label references look like @adnz//package
    name = "npm",
    args = [
        "--frozen-lockfile",
        "--ignore-engines",
    ],
    exports_directories_only = True,
    package_json = "//:package.json",
    yarn_lock = "//:yarn.lock",
    symlink_node_modules = True,
)
