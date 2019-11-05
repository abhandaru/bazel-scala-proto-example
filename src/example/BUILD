load('@io_bazel_rules_scala//scala:scala.bzl', 'scala_library')

scala_library(
  name='example',
  srcs=glob(['*.scala']),
  deps=[
    '//src/protobuf:scala'
  ]
)
