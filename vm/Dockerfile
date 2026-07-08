FROM ubuntu:24.04

# Hindari prompt interaktif saat instalasi paket
ENV DEBIAN_FRONTEND=noninteractive

# Update dan install OpenSSH server, sudo, serta python3
RUN apt-get update && apt-get install -y \
    openssh-server \
    sudo \
    python3 \
    && rm -rf /var/lib/apt/lists/*

# Konfigurasi direktori SSH daemon
RUN mkdir -p /run/sshd

# Membuat user 'deploy' dan mengatur konfigurasi sudo tanpa password
RUN useradd -m -s /bin/bash deploy && \
    echo 'deploy ALL=(ALL) NOPASSWD:ALL' > /etc/sudoers.d/deploy && \
    chmod 0440 /etc/sudoers.d/deploy

# Membuat direktori .ssh untuk user deploy
RUN mkdir -p /home/deploy/.ssh && \
    chown -R deploy:deploy /home/deploy/.ssh

# Membuka port 22 di dalam kontainer
EXPOSE 22

# Menjalankan SSH daemon saat kontainer dimulai
CMD ["/usr/sbin/sshd", "-D"]
