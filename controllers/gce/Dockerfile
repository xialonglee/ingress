# Copyright 2015 The Kubernetes Authors. All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

# TODO: use radial/busyboxplus:curl or alping instead
FROM ubuntu:14.04
MAINTAINER Prashanth B <beeps@google.com>

# so apt-get doesn't complain
ENV DEBIAN_FRONTEND=noninteractive
RUN sed -i 's/^exit 101/exit 0/' /usr/sbin/policy-rc.d

# TODO: Move to using haproxy:1.5 image instead. Honestly,
# that image isn't much smaller and the convenience of having
# an ubuntu container for dev purposes trumps the tiny amounts
# of disk and bandwidth we'd save in doing so.
RUN \
  apt-get update && \
  apt-get install -y ca-certificates && \
  apt-get install -y curl && \
  rm -rf /var/lib/apt/lists/*

ADD glbc glbc
ENTRYPOINT ["/glbc"]
