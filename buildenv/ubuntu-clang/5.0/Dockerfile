FROM walberla/buildenv-ubuntu-basic:17.10

RUN apt-get update &&  apt-get install  -y \
    libomp-dev \
    libbz2-dev \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/* 

RUN cd /usr/local \
 && curl -L http://releases.llvm.org/5.0.0/clang+llvm-5.0.0-x86_64-linux-gnu-ubuntu-16.04.tar.xz | tar --strip-components=1 -xJ

 
RUN update-alternatives --install /usr/bin/clang   clang   /usr/local/bin/clang 999 \
 && update-alternatives --install /usr/bin/clang++ clang++ /usr/local/bin/clang++ 999 \
 && update-alternatives --install /usr/bin/cc  cc  /usr/local/bin/clang 999 \
 && update-alternatives --install /usr/bin/c++ c++ /usr/local/bin/clang++ 999

RUN cd /tmp \
 && mkdir boost \
 && cd boost \
 && curl -L http://downloads.sourceforge.net/project/boost/boost/1.66.0/boost_1_66_0.tar.bz2 | tar xj \
 && cd boost_1_66_0 \
 && ./bootstrap.sh --with-python=/usr/bin/python3 \
 && ./b2 -j $(nproc) toolset=clang install --prefix=/opt/boost \
 && cd \
 && rm -r /tmp/boost

ENV BOOST_ROOT="/opt/boost"
 
ENV CC="ccache clang" CXX="ccache clang++"

