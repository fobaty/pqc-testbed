Last login: Sat Apr 19 21:34:42 on console
fobaty@Macbook ~ % ssh jupiter
Welcome to Ubuntu 24.10 (GNU/Linux 6.11.0-1007-raspi aarch64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Sat Apr 19 21:42:18 PDT 2025

  System load:           0.1
  Usage of /:            28.2% of 57.97GB
  Memory usage:          25%
  Swap usage:            0%
  Temperature:           52.6 C
  Processes:             276
  Users logged in:       1
  IPv4 address for eth0: 192.168.1.100
  IPv6 address for eth0: 2600:1700:5a6a:8210::2b
  IPv6 address for eth0: 2600:1700:5a6a:8210:da3a:ddff:fe24:11b6

 * Strictly confined Kubernetes makes edge and IoT secure. Learn how MicroK8s
   just raised the bar for easy, resilient and secure K8s cluster deployment.

   https://ubuntu.com/engage/secure-kubernetes-at-the-edge

0 updates can be applied immediately.


*** System restart required ***
Last login: Sat Apr 19 16:31:14 2025 from 192.168.1.77
pi@jupiter:~$ cd docker/
composes/    influxdb/    pqc-testbed/ shatsys/     tig-stack/   traefik/
pi@jupiter:~$ cd docker/pqc-testbed/
pi@jupiter:~/docker/pqc-testbed$ cd server/
pi@jupiter:~/docker/pqc-testbed/server$ nano Dockerfile 

  GNU nano 8.1                       Dockerfile                                 
    make -j$(nproc) && make install && \
    # Create symlink for libssl if not already created by installer
    if [ -f "$OQS_OPENSSL_DIR/lib/libssl.so.1.1" ]; then \
        ln -sf $OQS_OPENSSL_DIR/lib/libssl.so.1.1 $OQS_OPENSSL_DIR/lib/libssl.s>
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
