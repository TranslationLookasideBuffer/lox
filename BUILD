load("@bazel_tools//tools/jdk:default_java_toolchain.bzl", "BASE_JDK9_JVM_OPTS", "DEFAULT_JAVACOPTS", "DEFAULT_TOOLCHAIN_CONFIGURATION", "default_java_toolchain")

default_java_toolchain(
    name = "repository_default_toolchain",
    configuration = DEFAULT_TOOLCHAIN_CONFIGURATION,
    java_runtime = "@bazel_tools//tools/jdk:remotejdk_20",
    javacopts = DEFAULT_JAVACOPTS + ["--enable-preview"],
    jvm_opts = BASE_JDK9_JVM_OPTS + ["--enable-preview"],
    source_version = "20",
    target_version = "20",
)
