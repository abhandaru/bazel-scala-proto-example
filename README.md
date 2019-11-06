# bazel-scala-proto-example

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
bazel build //src/example
```
