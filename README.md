# lox

[![License](https://img.shields.io/github/license/TranslationLookasideBuffer/lox)](LICENSE)

A repo that mostly follows [Crafting Interpreters](https://craftinginterpreters.com).

## Setup

### Bazel

This repository uses [Bazel](https://bazel.build) for build and dependency management.

This document assumes that [bazelisk](https://github.com/bazelbuild/bazelisk) is used instead of
Bazel directly. See [these instructions](https://github.com/bazelbuild/bazelisk#requirements) for
installing this tool via `go`.

The entire project can be built with `bazelisk build ...:all` from the root of the repository.

#### Dependencies

Dependencies are configured in the [`WORKSPACE`](WORKSPACE) file and the
[`third_party`](src/main/third_party) directory. Dependencies defined in the former (generally as
part of the `maven_install` rule) and are wrapped in `java_library` targets in the latter. This
makes their usage throughout the codebase much cleaner.

#### Tools

It is recommended that several tools are also used.

##### [Buildifier](https://github.com/bazelbuild/buildtools/blob/master/buildifier/README.md)

Handles auto-formatting of all `BUILD` and `WORKSPACE` files. From the root of the repository,
`buildifier -r -lint=fix -v .` will fix all files automatically.

This tool should be installed via `go install`.

##### [Unused Deps](https://github.com/bazelbuild/buildtools/blob/master/unused_deps/README.md)

Searches for unused dependencies in `java_library` rules. From the root of the repository,
`unused_deps --build_tool=bazelisk ...:all` will analyze all relevant targets.

This tool should be installed via `go install`.

##### [Buildozer](https://github.com/bazelbuild/buildtools/blob/master/buildozer/README.md)

Rewrites `BUILD` files based on standard commands. Most usages will be copied from the output
of an Unused Deps command.

This tool should be installed via `go install`.

##### [Google Java Format](https://github.com/google/google-java-format)

Automatically formats Java source files according to the
[Google Java Style Guide](https://google.github.io/styleguide/javaguide.html). From the root of the
repository (and on Linux), the following command will format all Java source files:

```
bazelisk run src/main/third_party/tools:java_format -- \
  --replace $(find ~+ -not -path '*/\.*' -type f -name '*.java')
```

Unlike the previous tools, this tool can be run without installing anything.