load('@io_bazel_rules_scala//scala_proto:scala_proto.bzl', 'scalapb_proto_library')

proto_library(
  name='protobuf',
  srcs=glob(['*.proto']),
)

scalapb_proto_library(
  name='scala',
  deps=[':protobuf'],
  visibility=['//visibility:public'],
)
