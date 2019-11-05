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
bazel build //src/example --incompatible_disable_deprecated_attr_params=false --incompatible_depset_is_not_iterable=false --incompatible_no_support_tools_in_action_inputs=false
INFO: Analyzed target //src/example:example (67 packages loaded, 1239 targets configured).
INFO: Found 1 target...
INFO: From Building external/com_google_protobuf/libprotobuf_java.jar (78 source files, 1 source jar):
warning: -parameters is not supported for target value 1.7. Use 1.8 or later.
INFO: From Building external/com_google_protobuf/libprotobuf_java.jar (78 source files, 1 source jar) [for host]:
warning: -parameters is not supported for target value 1.7. Use 1.8 or later.
INFO: From scala @io_bazel_rules_scala//src/scala/scripts:scalapb_generator_lib [for host]:
warning: there were two deprecation warnings (since 2.11.0); re-run with -deprecation for details
one warning found
ERROR: /Users/adu/workspace/bazel-scala-proto-example/src/example/BUILD:3:1: scala //src/example:example failed (Exit 1)
src/example/Example.scala:3: error: object Person is not a member of package adu.protobuf
import adu.protobuf.Person
       ^
src/example/Example.scala:6: error: not found: value Person
  val Me = Person()
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
INFO: Elapsed time: 167.688s, Critical Path: 72.38s
INFO: 217 processes: 202 darwin-sandbox, 15 worker.
FAILED: Build did NOT complete successfully
```
