FROM cjxd/buildenv-ubuntu-basic:24.04

ENV CLANG_VERSION=17

RUN apt-get update && apt-get install -y \
    lsb-release \
    wget \
    software-properties-common \
    gnupg \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/* 

RUN curl -so llvm.sh https://apt.llvm.org/llvm.sh \
 && bash llvm.sh $CLANG_VERSION \
 && rm llvm.sh

