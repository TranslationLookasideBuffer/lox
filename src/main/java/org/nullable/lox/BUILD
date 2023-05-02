java_library(
    name = "lox",
    srcs = glob(["*.java"]) + ["//src/main/java/org/nullable/lox/tool:generate_ast"],
)

java_binary(
    name = "jlox",
    main_class = "org.nullable.lox.Lox",
    runtime_deps = [":lox"],
)
