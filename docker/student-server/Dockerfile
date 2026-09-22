FROM ubuntu:24.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    openssh-server \
    sudo \
    iproute2 \
    iputils-ping \
    curl \
    net-tools \
    nano \
    vim \
    dnsutils \
    traceroute \
    procps \
    rsync \
    && rm -rf /var/lib/apt/lists/*

RUN useradd -m -s /bin/bash student \
    && echo 'student:student' | chpasswd \
    && usermod -aG sudo student \
    && echo 'student ALL=(ALL) NOPASSWD:ALL' > /etc/sudoers.d/student


RUN mkdir -p /backups && chown student:student /backups

RUN mkdir -p /run/sshd

CMD ["/usr/sbin/sshd", "-D"]


