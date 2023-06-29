load("@bazel_skylib//rules:run_binary.bzl", "run_binary")

package(default_visibility = ["//src/main/java/org/nullable/lox:__pkg__"])

java_binary(
    name = "generate_ast_binary",
    srcs = ["GenerateAst.java"],
    main_class = "org.nullable.lox.tool.GenerateAst",
    visibility = ["//visibility:private"],
)

run_binary(
    name = "generate_ast",
    outs = [
        "Expr.java",
        "Stmt.java",
    ],
    args = ["$(location Expr.java)"],
    tool = ":generate_ast_binary",
)
