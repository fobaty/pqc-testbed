# Use a minimal base image with required build tools
FROM debian:bullseye-slim

# Set environment variables
ENV DEBIAN_FRONTEND=noninteractive
ENV OQS_OPENSSL_DIR=/opt/oqs-openssl

# Install necessary dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    git \
    cmake \
    ninja-build \
    python3 \
    python3-pip \
    libssl-dev \
    perl \
    wget \
    curl \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*

# Install Python dependencies (if needed)
RUN pip3 install --no-cache-dir cryptography

# Create a working directory
WORKDIR /root

# Clone and build liboqs (Quantum-Safe Crypto library)
RUN git clone --branch main https://github.com/open-quantum-safe/liboqs.git && \
    cd liboqs && \
    mkdir build && cd build && \
    cmake -GNinja -DOQS_USE_OPENSSL=OFF -DCMAKE_INSTALL_PREFIX=/opt/liboqs .. && \
    ninja && ninja install

# Clone and build OQS-OpenSSL with architecture-specific target
RUN git clone --branch OQS-OpenSSL_1_1_1-stable https://github.com/open-quantum-safe/openssl.git >
    cd openssl && \
    ARCH=$(uname -m) && \
    if [ "$ARCH" = "aarch64" ]; then TARGET="linux-aarch64"; \
    elif [ "$ARCH" = "x86_64" ]; then TARGET="linux-x86_64"; \
    else echo "Unsupported architecture: $ARCH" && exit 1; fi && \
    ./Configure --prefix=$OQS_OPENSSL_DIR --openssldir=$OQS_OPENSSL_DIR $TARGET -lm && \
    make -j$(nproc) && make install && \
    # Create symlink for libssl if not already created by installer
    if [ -f "$OQS_OPENSSL_DIR/lib/libssl.so.1.1" ]; then \
        ln -sf $OQS_OPENSSL_DIR/lib/libssl.so.1.1 $OQS_OPENSSL_DIR/lib/libssl.so; \
    fi

# Add OpenSSL binary path to environment
ENV PATH="$OQS_OPENSSL_DIR/bin:$PATH"
ENV LD_LIBRARY_PATH="$OQS_OPENSSL_DIR/lib:$LD_LIBRARY_PATH"

# Print versions for verification
RUN openssl version -a && \
    echo "Build completed for architecture: $(uname -m)"

# Set working directory to optional app directory (you can change this)
WORKDIR /app

# Default command (you can replace this with your application startup command)
CMD [ "bash" ]
