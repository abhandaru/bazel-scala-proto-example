scala_version='2.12.6'
rules_scala_version='7bc18d07001cbfd425c6761c8384c4e982d25a2b' # update this as needed

load('@bazel_tools//tools/build_defs/repo:http.bzl', 'http_archive')
http_archive(
  name='io_bazel_rules_scala',
  url='https://github.com/bazelbuild/rules_scala/archive/%s.zip' % rules_scala_version,
  type='zip',
  strip_prefix='rules_scala-%s' % rules_scala_version
)

http_archive(
  name='rules_proto',
  sha256='57001a3b33ec690a175cdf0698243431ef27233017b9bed23f96d44b9c98242f',
  strip_prefix='rules_proto-9cd4f8f1ede19d81c6d48910429fe96776e567b1',
  urls=[
    'https://mirror.bazel.build/github.com/bazelbuild/rules_proto/archive/9cd4f8f1ede19d81c6d48910429fe96776e567b1.tar.gz',
    'https://github.com/bazelbuild/rules_proto/archive/9cd4f8f1ede19d81c6d48910429fe96776e567b1.tar.gz',
  ],
)

load('@io_bazel_rules_scala//scala:scala.bzl', 'scala_repositories')
scala_repositories((scala_version, {
  'scala_compiler': '3023b07cc02f2b0217b2c04f8e636b396130b3a8544a8dfad498a19c3e57a863',
  'scala_library': 'f81d7144f0ce1b8123335b72ba39003c4be2870767aca15dd0888ba3dab65e98',
  'scala_reflect': 'ffa70d522fc9f9deec14358aa674e6dd75c9dfa39d4668ef15bb52f002ce99fa'
}))

load('@io_bazel_rules_scala//scala:toolchains.bzl', 'scala_register_toolchains')
scala_register_toolchains()

load('@io_bazel_rules_scala//scala_proto:scala_proto.bzl', 'scala_proto_repositories')
scala_proto_repositories(scala_version=scala_version)

load('@io_bazel_rules_scala//scala_proto:toolchains.bzl', 'scala_proto_register_toolchains')
scala_proto_register_toolchains()

load('@rules_proto//proto:repositories.bzl', 'rules_proto_dependencies', 'rules_proto_toolchains')
rules_proto_dependencies()
rules_proto_toolchains()
