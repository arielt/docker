FROM ubuntu:16.04
MAINTAINER Ariel Tubaltsev

# Add Clang-Format to the repository sources list
RUN echo 'deb http://apt.llvm.org/xenial/ llvm-toolchain-xenial-5.0 main' | tee /etc/apt/sources.list.d/clang.list

# Update the repository
RUN apt-get update

# Install clang-format
RUN apt-get install -y --allow-unauthenticated clang-format-5.0

# 2 binaries we need:
#    clang-format-5.0
#    clang-format-diff-5.0
