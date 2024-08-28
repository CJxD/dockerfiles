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

RUN update-alternatives --install /usr/bin/clang   clang   /usr/bin/clang-$CLANG_VERSION 999 \
 && update-alternatives --install /usr/bin/clang++ clang++ /usr/bin/clang++-$CLANG_VERSION 999 \
 && update-alternatives --install /usr/bin/cc  cc  /usr/bin/clang-$CLANG_VERSION 999 \
 && update-alternatives --install /usr/bin/c++ c++ /usr/bin/clang++-$CLANG_VERSION 999

