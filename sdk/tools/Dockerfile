FROM ubuntu:latest

LABEL io.github.geekswamp.image.souce https://github.com/geekswamp/docker-android-sdk
LABEL org.opencontainers.image.source https://github.com/geekswamp/docker-android-sdk
LABEL org.opencontainers.image.description Android Command Line Tools on Ubuntu Linux
LABEL org.opencontainers.image.licenses MIT

ENV ANDROID_SDK_TOOLS_VERSION 11076708
ENV ANDROID_HOME /opt/Android/Sdk
ENV ANDROID_PLATFORM_VERSION 34
ENV ANDROID_BUILD_TOOLS_VERSION 34.0.0
ENV ANDROID_BUILD_TOOLS_ROOT ${ANDROID_HOME}/cmdline-tools/latest
ENV JAVA_HOME /usr/lib/jvm/java-21-openjdk-amd64
ENV PATH "$PATH:$ANDROID_BUILD_TOOLS_ROOT/bin:$ANDROID_HOME/platform-tools:$JAVA_HOME/bin"

RUN set -eux; mkdir .android && touch .android/repositories.cfg \
  && apt-get update && apt-get upgrade -y \ 
  && apt-get install git zip make unzip lcov curl xz-utils libglu1-mesa openjdk-21-jdk --no-install-recommends -y \
  && curl https://dl.google.com/android/repository/commandlinetools-linux-${ANDROID_SDK_TOOLS_VERSION}_latest.zip -o sdk-tools.zip \
  && mkdir -p ${ANDROID_HOME}/cmdline-tools \
  && unzip -q sdk-tools.zip -d ${ANDROID_HOME}/cmdline-tools \
  && rm sdk-tools.zip \
  && mv ${ANDROID_HOME}/cmdline-tools/cmdline-tools ${ANDROID_BUILD_TOOLS_ROOT} \
  && apt purge unzip -y \
  && apt-get autoremove \
  && apt-get autoclean

RUN set -eux; yes | sdkmanager --licenses \
  && sdkmanager "build-tools;$ANDROID_BUILD_TOOLS_VERSION" "platform-tools" \
  "platforms;android-$ANDROID_PLATFORM_VERSION"
