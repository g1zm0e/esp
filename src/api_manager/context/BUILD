# Copyright (C) Extensible Service Proxy Authors. All Rights Reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#    http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
################################################################################
#
package(default_visibility = ["//src/api_manager:__subpackages__"])

cc_library(
    name = "context",
    srcs = [
        "global_context.cc",
        "request_context.cc",
        "service_context.cc",
    ],
    hdrs = [
        "global_context.h",
        "request_context.h",
        "service_context.h",
    ],
    linkopts = select({
        "//:darwin": [],
        "//conditions:default": [
            "-lm",
            "-luuid",
        ],
    }),
    deps = [
        "//external:cc_wkt_protos",
        "//external:cloud_trace",
        "//external:googletest_prod",
        "//external:grpc++",
        "//external:protobuf",
        "//external:service_config",
        "//external:servicecontrol",
        "//external:servicecontrol_client",
        "//src/api_manager:http_template",
        "//src/api_manager:impl_headers",
        "//src/api_manager:path_matcher",
        "//src/api_manager:server_config_proto",
        "//src/api_manager/auth",
        "//src/api_manager/auth:authz",
        "//src/api_manager/auth:service_account_token",
        "//src/api_manager/cloud_trace",
        "//src/api_manager:compute_platform",
        "//src/api_manager/service_control",
        "//src/api_manager/utils",
    ],
)

cc_test(
    name = "client_ip_extraction_test",
    size = "small",
    srcs = [
        "client_ip_extraction_test.cc",
    ],
    deps = [
        "//external:googletest_main",
        "//src/api_manager",
    ],
)

cc_test(
    name = "global_context_test",
    size = "small",
    srcs = [
        "global_context_test.cc",
    ],
    deps = [
        "//external:googletest_main",
        "//src/api_manager",
        "//src/api_manager:compute_platform",
        "//src/api_manager:mock_api_manager_environment",
    ],
)
