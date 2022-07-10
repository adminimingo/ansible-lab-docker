FROM ubuntu:jammy-20220531
LABEL maintainer="leo"

RUN apt update && apt upgrade -y \
  && DEBIAN_FRONTEND=noninteractive \
  && apt install -y apt --no-install-recommends \
  openssh-server python3 python3-distutils iputils-ping nano locales tzdata \
  && sed -i 's/^#PermitRootLogin prohibit-password/PermitRootLogin yes/1' /etc/ssh/sshd_config \
  && echo 'root:toor' | chpasswd \
  && mkdir /run/sshd \
  && sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen \
  && dpkg-reconfigure --frontend=noninteractive locales \
  && update-locale LANG=en_US.UTF-8 \
  && ln -snf /usr/share/zoneinfo/Europe/Paris /etc/localtime && echo Europe/Paris > /etc/timezone \
  && apt autoclean && rm -rf /tmp/* /var/tmp/*

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
