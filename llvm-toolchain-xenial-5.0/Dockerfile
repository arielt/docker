FROM ubuntu:16.04
MAINTAINER Ariel Tubaltsev

# Provides: clang-format, clang-format-diff, clang-tidy, clang-check

# Singe RUN command to bust the cache.
#
# Update sources list, update repository, install wget and retrieve archive
# signature.
#
# Install clang packages
RUN echo 'deb http://apt.llvm.org/xenial/ llvm-toolchain-xenial-5.0 main' | tee /etc/apt/sources.list.d/clang.list && \
    echo 'deb-src http://apt.llvm.org/xenial/ llvm-toolchain-xenial-5.0 main' | tee -a /etc/apt/sources.list.d/clang.list && \
    apt-get update && \
    apt-get install -y --no-install-recommends apt-utils && \
    apt-get install -y wget && \
    wget -O - https://apt.llvm.org/llvm-snapshot.gpg.key | apt-key add - && \
    apt-get update && \
    apt-get install -y clang-5.0 clang-5.0-doc libclang-common-5.0-dev \
    libclang-5.0-dev libclang1-5.0 libclang1-5.0-dbg \
    libllvm5.0 libllvm5.0-dbg lldb-5.0 llvm-5.0 llvm-5.0-dev llvm-5.0-doc \
    llvm-5.0-examples llvm-5.0-runtime clang-format-5.0 python-clang-5.0 \
    liblldb-5.0-dev lld-5.0 libfuzzer-5.0-dev \
    clang-tidy-5.0 && \
    ln -s /usr/bin/clang-format-5.0 /usr/bin/clang-format && \
    ln -s /usr/bin/clang-format-diff-5.0 /usr/bin/clang-format-diff && \
    ln -s /usr/bin/clang-tidy-5.0 /usr/bin/clang-tidy && \
    ln -s /usr/bin/clang-check-5.0 /usr/bin/clang-check
