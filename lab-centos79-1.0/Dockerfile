FROM centos:centos7.9.2009
LABEL maintainer="leo"

#Timezone
ENV TZ=Europe/Paris
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN yum update -y
COPY systemctl3.py /usr/bin/systemctl
RUN chmod 755 /usr/bin/systemctl && chown root:root /usr/bin/systemctl

RUN yum install -y openssh-server python3 \
&&  yum clean all \
&&  sed -i 's/#PermitRootLogin yes/PermitRootLogin yes/' /etc/ssh/sshd_config \
&&  echo 'root:toor' | chpasswd \
&&  mkdir /run/sshd \
&&  ssh-keygen -A

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
