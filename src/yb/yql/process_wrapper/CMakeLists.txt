# Copyright (c) YugabyteDB, Inc.
#
# Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except
# in compliance with the License.  You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software distributed under the License
# is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express
# or implied.  See the License for the specific language governing permissions and limitations
# under the License.
#

set(PROCESS_WRAPPER_SRCS
    process_wrapper.cc
    common_config.cc)
set(PROCESS_WRAPPER_LIBS
    yb_util)
ADD_YB_LIBRARY(yb_process_wrapper
               SRCS ${PROCESS_WRAPPER_SRCS}
               DEPS ${PROCESS_WRAPPER_LIBS})
ADD_YB_LIBRARY(yb_process_wrapper_minimal
               SRCS process_wrapper.cc
               DEPS ${PROCESS_WRAPPER_LIBS})

set(YB_TEST_LINK_LIBS
  gmock
  gtest
  gutil
  yb_process_wrapper_minimal
  server_process
  yb_util
  ${YB_MIN_TEST_LIBS})

ADD_YB_TEST(process_wrapper-test)
