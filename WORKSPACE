load("@bazel_tools//tools/build_defs/repo:git.bzl", "new_git_repository")

new_git_repository(
    name = "skicka",
    remote = "https://github.com/google/skicka.git",
    branch = "master",
    build_file = "@//:BUILD.skicka",
)

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

RULES_GO_VER = "0.22.4"
RULES_GO_SHA256 = "7b9bbe3ea1fccb46dcfa6c3f3e29ba7ec740d8733370e21cdc8937467b4a4349"

http_archive(
    name = "io_bazel_rules_go",
    sha256 = RULES_GO_SHA256,
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_go/releases/download/v%s/rules_go-v%s.tar.gz" % (RULES_GO_VER, RULES_GO_VER),
        "https://github.com/bazelbuild/rules_go/releases/download/v%s/rules_go-v%s.tar.gz" % (RULES_GO_VER, RULES_GO_VER),
    ],
)

BAZEL_GAZELLE_VER = "0.20.0"
BAZEL_GAZELLE_SHA256 = "d8c45ee70ec39a57e7a05e5027c32b1576cc7f16d9dd37135b0eddde45cf1b10"

http_archive(
    name = "bazel_gazelle",
    sha256 = BAZEL_GAZELLE_SHA256,
    urls = [
        "https://storage.googleapis.com/bazel-mirror/github.com/bazelbuild/bazel-gazelle/releases/download/v%s/bazel-gazelle-v%s.tar.gz" % (BAZEL_GAZELLE_VER, BAZEL_GAZELLE_VER),
        "https://github.com/bazelbuild/bazel-gazelle/releases/download/v%s/bazel-gazelle-v%s.tar.gz" % (BAZEL_GAZELLE_VER, BAZEL_GAZELLE_VER),
    ],
)

load(
    "@io_bazel_rules_go//go:deps.bzl",
    "go_download_sdk",
    "go_rules_dependencies",
    "go_register_toolchains",
)

go_download_sdk(
    name = "go_sdk",
    goos = "linux",
    goarch = "amd64",
    version = "1.14.2",
)

go_rules_dependencies()

go_register_toolchains()

load("@bazel_gazelle//:deps.bzl", "gazelle_dependencies")

gazelle_dependencies()

PROTOBUF_VER = "3.11.4"
PROTOBUF_SHA256 = "a79d19dcdf9139fa4b81206e318e33d245c4c9da1ffed21c87288ed4380426f9"

http_archive(
    name = "com_google_protobuf",
    sha256 = PROTOBUF_SHA256,
    urls = [
        "https://github.com/protocolbuffers/protobuf/archive/v%s.tar.gz" % PROTOBUF_VER,
    ],
    strip_prefix = "protobuf-%s" % PROTOBUF_VER
)

load("@com_google_protobuf//:protobuf_deps.bzl", "protobuf_deps")

protobuf_deps()

http_archive(
    name = "rules_proto",
    sha256 = "2490dca4f249b8a9a3ab07bd1ba6eca085aaf8e45a734af92aad0c42d9dc7aaf",
    strip_prefix = "rules_proto-218ffa7dfa5408492dc86c01ee637614f8695c45",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_proto/archive/218ffa7dfa5408492dc86c01ee637614f8695c45.tar.gz",
        "https://github.com/bazelbuild/rules_proto/archive/218ffa7dfa5408492dc86c01ee637614f8695c45.tar.gz",
    ],
)

load("@rules_proto//proto:repositories.bzl", "rules_proto_dependencies", "rules_proto_toolchains")

rules_proto_dependencies()

rules_proto_toolchains()

load("//:skicka_repos.bzl", "skicka_go_repositories")

skicka_go_repositories()