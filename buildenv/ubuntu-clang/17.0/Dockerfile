FROM cjxd/buildenv-ubuntu-basic:24.04

ENV CLANG_VERSION=17

RUN echo "deb http://apt.llvm.org/noble/ llvm-toolchain-noble main" > /etc/apt/sources.list.d/llvm-toolchain.list && curl -s https://apt.llvm.org/llvm-snapshot.gpg.key | apt-key add -

RUN apt-get update && apt-get install -y \
    clang-$CLANG_VERSION \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/* 
 
RUN update-alternatives --install /usr/bin/clang   clang   /usr/bin/clang-$CLANG_VERSION 999 \
 && update-alternatives --install /usr/bin/clang++ clang++ /usr/bin/clang++-$CLANG_VERSION 999 \
 && update-alternatives --install /usr/bin/cc  cc  /usr/bin/clang-$CLANG_VERSION 999 \
 && update-alternatives --install /usr/bin/c++ c++ /usr/bin/clang++-$CLANG_VERSION 999
