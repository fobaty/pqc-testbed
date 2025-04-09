FROM ubuntu:22.04

RUN apt update && \
    apt install -y build-essential git cmake curl

# Установка liboqs и OpenSSL с поддержкой PQC
WORKDIR /root
RUN git clone --branch OQS-OpenSSL_1_1_1-stable https://github.com/open-quantum-safe/openssl.git && \
    git clone https://github.com/open-quantum-safe/liboqs.git && \
    cd liboqs && mkdir build && cd build && cmake .. && make -j$(nproc) && make install && \
    cd ../../openssl && ./config --prefix=/opt/oqs-openssl --openssldir=/opt/oqs-openssl && \
    make -j$(nproc) && make install

# Использовать curl с указанной версией OpenSSL
ENV LD_LIBRARY_PATH=/opt/oqs-openssl/lib
