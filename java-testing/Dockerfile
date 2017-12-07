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

FROM ubuntu:xenial

# Install utilities + openjdk-8
RUN apt-get update \
    && apt-get -y upgrade \
    && apt-get -y install \
      unzip \
      wget \
      curl \
      git \
      openssl \
      python \
      openjdk-8-jdk \
      software-properties-common \
    && update-alternatives --set java /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java \
    && apt-get clean

# Install GCloud (requires python)
RUN curl https://sdk.cloud.google.com > cloudsdk.sh \
    && chmod +x cloudsdk.sh \
    && ./cloudsdk.sh --disable-prompts --install-dir=/opt \
    && /opt/google-cloud-sdk/bin/gcloud components install --quiet \
      app-engine-java \
      cbt \
      kubectl \
      alpha \
      beta
ENV PATH="/opt/google-cloud-sdk/bin:${PATH}"

# Install Maven
RUN wget http://www-us.apache.org/dist/maven/maven-3/3.5.2/binaries/apache-maven-3.5.2-bin.zip \
   && unzip apache-maven-3.5.2-bin.zip \
   && rm apache-maven-3.5.2-bin.zip \
   && mv apache-maven-3.5.2 /opt/maven
ENV PATH="/opt/maven/bin:${PATH}"

# Install Gradle
RUN wget https://services.gradle.org/distributions/gradle-4.3-bin.zip \
    && unzip gradle-4.3-bin.zip \
    && rm gradle-4.3-bin.zip \
    && mv gradle-4.3 /opt/gradle \
    && GRADLE_HOME=/opt/gradle
ENV PATH="/opt/gradle/bin:${PATH}" 
    
