# Bug Report: ng_ts_library cannot build .tsx files

We have a repo whcih is a mix of Angular/React components, so we have both .tsx and .ts files co-existing.

Our current setup uses @angular-builders/custom-webpack:browser which correctly handles all of the files. We are trying to migrate to Bazel, but have run into a roadblock where `ng_ts_library` (using the example [here](https://github.com/bazelbuild/rules_nodejs/tree/master/examples/angular)) does not seem to correctly handle TSX files. Specifically:

- If the .tsx is built using the regular `ts_library` rule and added as a dependency to the `ng_ts_library` rule, everything works as intended (example: `bazel build :main_tsx_split`).
- If the .tsx is built using `ng_ts_library`, we get errors (example: `bazel build :main_tsx_combined` or `bazel build :main_tsx_split_ng`).

The output when running `bazel build :message_tsx_ng` is:

```
$ bazel build :message_tsx_ng
INFO: Analyzed target //:message_tsx_ng (108 packages loaded, 4871 targets configured).
INFO: Found 1 target...
ERROR: /home/jeshua/work/bazel-angular-react-example/BUILD:102:14: output 'message_tsx.ngfactory.js' was not created
ERROR: /home/jeshua/work/bazel-angular-react-example/BUILD:102:14: output 'message_tsx.ngsummary.js' was not created
ERROR: /home/jeshua/work/bazel-angular-react-example/BUILD:102:14: output 'message_tsx.ngfactory.d.ts' was not created
ERROR: /home/jeshua/work/bazel-angular-react-example/BUILD:102:14: output 'message_tsx.ngsummary.d.ts' was not created
ERROR: /home/jeshua/work/bazel-angular-react-example/BUILD:102:14: Compiling TypeScript (devmode) //:message_tsx_ng failed: not all outputs were created or valid
Target //:message_tsx_ng failed to build
Use --verbose_failures to see the command lines of failed build steps.
INFO: Elapsed time: 0.755s, Critical Path: 0.21s
INFO: 2 processes: 1 internal, 1 worker.
FAILED: Build did NOT complete successfully
```
