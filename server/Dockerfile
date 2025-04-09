FROM ubuntu:22.04

RUN apt update && \
    apt install -y build-essential git cmake nginx curl

# Установка OpenSSL с liboqs
WORKDIR /root
RUN git clone --branch OQS-OpenSSL_1_1_1-stable https://github.com/open-quantum-safe/openssl.git && \
    git clone https://github.com/open-quantum-safe/liboqs.git && \
    cd liboqs && mkdir build && cd build && cmake .. && make -j$(nproc) && make install && \
    cd ../../openssl && ./config --prefix=/opt/oqs-openssl --openssldir=/opt/oqs-openssl && \
    make -j$(nproc) && make install

# Создание самоподписанного сертификата
RUN /opt/oqs-openssl/bin/openssl req -x509 -newkey rsa:2048 -keyout /etc/ssl/private/server.key -out /etc/ssl/certs/server.crt -days 365 -nodes -subj "/CN=pqc-test"

# Копируем конфигурацию nginx
COPY nginx.conf /etc/nginx/nginx.conf

CMD ["nginx", "-g", "daemon off;"]
