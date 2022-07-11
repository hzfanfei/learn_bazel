load("@build_bazel_rules_apple//apple:ios.bzl", "ios_application")
load("@build_bazel_rules_swift//swift:swift.bzl", "swift_library")
load("@build_bazel_rules_ios//rules:framework.bzl", "apple_framework")
load(
    "@com_github_buildbuddy_io_rules_xcodeproj//xcodeproj:xcodeproj.bzl",
    "xcodeproj",
)

apple_framework(
    name = "SnapKit",
    srcs = [
         "SnapKit/*.swift",
    ],
)

objc_library(
    name = "UrlGetClasses",
    srcs = [
        "UrlGet/AppDelegate.m",
        "UrlGet/UrlGetViewController.m",
        "UrlGet/main.m",
    ],
    hdrs = glob(["UrlGet/*.h"]),
	deps = [":SnapKit"],
)

ios_application(
    name = "ios-app",
    bundle_id = "Google.UrlGet",
    families = [
        "iphone",
        "ipad",
    ],
    infoplists = [":UrlGet/UrlGet-Info.plist"],
    launch_storyboard = "UrlGet/UrlGetViewController.xib",
    minimum_os_version = "8.0",
    visibility = ["//visibility:public"],
    deps = [":UrlGetClasses"],
)

xcodeproj(
    name = "xcodeproj",
    project_name = "ios-app",
    targets = [
        ":ios-app",
    ],
    tags = ["manual"],
)

