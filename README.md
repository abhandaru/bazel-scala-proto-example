# bazel-scala-proto-example

**This is not a working example yet**
Simple example of protobuf and scala building together with bazel


### Bazel information
```
Starting local Bazel server and connecting to it...
Build label: 0.28.1
Build target: bazel-out/darwin-opt/bin/src/main/java/com/google/devtools/build/lib/bazel/BazelServer_deploy.jar
Build time: Fri Jul 19 15:22:50 2019 (1563549770)
Build timestamp: 1563549770
Build timestamp as int: 1563549770
```


### Build command

For this version of `bazel` and the `WORKSPACE` in its current state, I have to enable a few deprecations. Very possible some version bumps throughout would alleviate the complexity here.

```bash
bazel build //src/example \
  --incompatible_disable_deprecated_attr_params=false \
  --incompatible_depset_is_not_iterable=false \
  --incompatible_no_support_tools_in_action_inputs=false
```


### Current failure output

```
adu (master) bazel-scala-proto-example $ bazel build //src/example --incompatible_disable_deprecated_attr_params=false --incompatible_depset_is_not_iterable=false --incompatible_no_support_tools_in_action_inputs=false
INFO: Analyzed target //src/example:example (0 packages loaded, 0 targets configured).
INFO: Found 1 target...
ERROR: /Users/adu/workspace/bazel-scala-proto-example/src/example/BUILD:14:1: scala //src/example:example failed (Exit 1)
src/example/Example.scala:3: error: object Protos is not a member of package example
import example.Protos
       ^
src/example/Example.scala:6: error: not found: value Protos
  val Me = new Protos.Person()
               ^
two errors found
two errors found
java.lang.RuntimeException: Build failed
  at io.bazel.rulesscala.scalac.ScalacProcessor.compileScalaSources(ScalacProcessor.java:242)
  at io.bazel.rulesscala.scalac.ScalacProcessor.processRequest(ScalacProcessor.java:67)
  at io.bazel.rulesscala.worker.GenericWorker.runPersistentWorker(GenericWorker.java:45)
  at io.bazel.rulesscala.worker.GenericWorker.run(GenericWorker.java:111)
  at io.bazel.rulesscala.scalac.ScalaCInvoker.main(ScalaCInvoker.java:41)
Target //src/example:example failed to build
Use --verbose_failures to see the command lines of failed build steps.
INFO: Elapsed time: 0.409s, Critical Path: 0.14s
INFO: 0 processes.
FAILED: Build did NOT complete successfully
```
