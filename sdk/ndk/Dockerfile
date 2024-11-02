FROM ghcr.io/geekswamp/android-sdk:latest

LABEL org.opencontainers.image.source https://github.com/geekswamp/docker-android-sdk
LABEL org.opencontainers.image.description Android NDK on Ubuntu Linux
LABEL org.opencontainers.image.licenses MIT

ENV ANDROID_NDK_VERSION 26.3.11579264

RUN set -eux; yes | sdkmanager "ndk;$ANDROID_NDK_VERSION"
