# Copyright 2017 Google Inc.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

FROM ubuntu:artful

RUN apt-get update \
    && apt-get upgrade -y\
    && apt-get install -y \
      software-properties-common \
      curl \
      git \
      openssl \
      openjdk-8-jdk \
      maven \
      gradle \
      python \
      python3.6 \
      python3.6-dev \
    && apt-get clean

RUN curl https://sdk.cloud.google.com > cloudsdk.sh \
    && chmod +x cloudsdk.sh \
    && ./cloudsdk.sh --disable-prompts --install-dir=/ \
    && export PATH=/google-cloud-sdk/bin:$PATH \
    && gcloud components install --quiet \
      app-engine-java \
      cbt \
      kubectl \
      alpha \
      beta
