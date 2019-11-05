load('@io_bazel_rules_scala//scala:scala.bzl', 'scala_library')
load('@io_bazel_rules_scala//scala_proto:scala_proto.bzl', 'scalapb_proto_library')

proto_library(
  name='person_proto',
  srcs=['person.proto'],
)

scalapb_proto_library(
  name='person_proto_scala',
  deps=[':person_proto'],
)

scala_library(
  name='example',
  srcs=glob(['*.scala']),
  deps=[':person_proto_scala']
)
