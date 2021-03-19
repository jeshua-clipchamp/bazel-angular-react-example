load("@npm//@bazel/typescript:index.bzl", "ts_library")
load("//tools:angular_ts_library.bzl", "ng_ts_library")

###
### Building `main_ts_combined` shows that you can build multiple TS files using ng_ts_library.
###
### Works as intended.
###
ng_ts_library(
    name = "main_ts_combined",
    srcs = [
        "main_ts.ts",
        "message_ts.ts",
    ],
    tsconfig = "//:tsconfig.json",
)

###
### Building `main_ts_split` demonstrates that you can have a ng_ts_library depend on a ts_library
### that uses .ts files.
###
### Works as intended.
###
ng_ts_library(
    name = "main_ts_split",
    srcs = ["main_ts.ts"],
    tsconfig = "//:tsconfig.json",
    deps = [":message_ts"],
)

ts_library(
    name = "message_ts",
    srcs = ["message_ts.ts"],
    tsconfig = "//:tsconfig.json",
)

###
### Building `main_ts_split_ng` demonstrates that you can have a ng_ts_library depend on a ts_library
### that uses .ts files.
###
### Works as intended.
###
ng_ts_library(
    name = "main_ts_split_ng",
    srcs = ["main_ts.ts"],
    tsconfig = "//:tsconfig.json",
    deps = [":message_ts_ng"],
)

ng_ts_library(
    name = "message_ts_ng",
    srcs = ["message_ts.ts"],
    tsconfig = "//:tsconfig.json",
)

###
### Building `main_tsx_combined` shows that you can _not_ build .tsx and .ts files together using ng_ts_library.
###
### DOES NOT WORK.
###
ng_ts_library(
    name = "main_tsx_combined",
    srcs = [
        "main_tsx.ts",
        "message_tsx.tsx",
    ],
    tsconfig = "//:tsconfig.json",
)

###
### Building `main_tsx_split` demonstrates that you can have a ng_ts_library depend on a ts_library
### that uses .tsx files.
###
### Works as intended.
###
ng_ts_library(
    name = "main_tsx_split",
    srcs = ["main_tsx.ts"],
    tsconfig = "//:tsconfig.json",
    deps = [":message_tsx"],
)

ts_library(
    name = "message_tsx",
    srcs = ["message_tsx.tsx"],
    tsconfig = "//:tsconfig.json",
)

###
### Building `main_tsx_split` demonstrates that you can have a ng_ts_library depend on a ng_ts_library
### that uses .tsx files.
###
### DOES NOT WORK.
###
ng_ts_library(
    name = "main_tsx_split_ng",
    srcs = ["main_tsx.ts"],
    tsconfig = "//:tsconfig.json",
    deps = [":message_tsx_ng"],
)

ng_ts_library(
    name = "message_tsx_ng",
    srcs = ["message_tsx.tsx"],
    tsconfig = "//:tsconfig.json",
)
