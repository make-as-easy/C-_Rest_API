licenses(["notice"])

exports_files(["LICENSE.md"])

cc_library(
    name = "served",
    copts = [],
    srcs = [
        "src/served/methods_handler.cpp",
        "src/served/multiplexer.cpp",
        "src/served/parameters.cpp",
        "src/served/request.cpp",
        "src/served/request_parser.cpp",
        "src/served/request_parser_impl.cpp",
        "src/served/response.cpp",
        "src/served/uri.cpp",
        "src/served/uri.hpp",
        "src/served/mux/regex_matcher.cpp",
        "src/served/mux/static_matcher.cpp",
        "src/served/mux/variable_matcher.cpp",
        "src/served/net/connection.cpp",
        "src/served/net/connection_manager.cpp",
        "src/served/net/server.cpp",
        "src/served/plugins/access_log.cpp",
    ],
    hdrs = [
        ":servedversion",
        "src/served/methods_handler.hpp",
        "src/served/methods.hpp",
        "src/served/multiplexer.hpp",
        "src/served/parameters.hpp",
        "src/served/plugins.hpp",
        "src/served/request_error.hpp",
        "src/served/request.hpp",
        "src/served/request_parser.hpp",
        "src/served/request_parser_impl.hpp",
        "src/served/response.hpp",
        "src/served/served.hpp",
        "src/served/status.hpp",
        "src/served/uri.hpp",
        "src/served/mux/empty_matcher.hpp",
        "src/served/mux/matchers.hpp",
        "src/served/mux/regex_matcher.hpp",
        "src/served/mux/segment_matcher.hpp",
        "src/served/mux/static_matcher.hpp",
        "src/served/mux/variable_matcher.hpp",
        "src/served/net/connection.hpp",
        "src/served/net/connection_manager.hpp",
        "src/served/net/server.hpp",
    ],
    defines = select({
        "@bazel_tools//src/conditions:windows": ["NOGDI"],
        "//conditions:default": [],
    }),
    strip_include_prefix = "src/",
    visibility = ["//visibility:public"],
    deps = [
        "@boost//:system",
        "@boost//:asio",
        "@boost//:date_time",
    ],
)

cc_binary(
    name = "example-handlers",
    copts = ["-Isrc",],
    srcs = [
        "src/examples/handlers/main.cpp",
    ],
    deps = [ "//:served" ],
)


genrule(
    name = "servedversion",
    srcs = [],
    outs = ["src/served/version.hpp"],
    cmd = """
echo '#ifndef SERVED_VERSION_HPP_INCLUDED' > $@
echo '#define SERVED_VERSION_HPP_INCLUDED' >> $@
echo '#define APPLICATION_NAME \"Served HTTP REST Library\"' >> $@
echo '#define APPLICATION_CODENAME \"served\"' >> $@
echo '#define APPLICATION_COPYRIGHT_YEARS \"2014\"' >> $@
echo '#define APPLICATION_VERSION_STRING \"1.4.3-DS1\"' >> $@
echo '#define APPLICATION_VENDOR_ID \"com.meltwater\"' >> $@
echo '#define APPLICATION_VENDOR_NAME \"Meltwater\"' >> $@
echo '#define APPLICATION_VENDOR_URL \"meltwater.com\"' >> $@
echo '#define APPLICATION_ID = \"com.meltwater.served\"' >> $@
echo '#endif' >> $@
  """,
)
