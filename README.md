# Bazel packaging sample

This sample is to craete executable binary from external repositories and make `deb` packages that include those executables for my persoanl use.

## List of projects

* [google/skicka](https://github.com/google/skicka)

## What I tried

### google/skicka

1. Run `go mod init github.com/google/skicka` to create `go.mod` file for the sake of easy generation of dependency config for Bazel
2. `gazelle -go_prefix github.com/google/skicka` to generate base `BUILD.skicka` that is mentioned in `new_git_repository` in `WORKSPACE`.
3. `gazelle update-repos -from_file go.mod -to_macro=skicka_repos.bzl%skicka_go_repositories` to generate `skicka_repos.bzl`.
4. Hand edit on `BUILD.skicka` to resolve local subpackages and change versions in packages fetched via `skicka_repos.bzl` to resolve build errors.