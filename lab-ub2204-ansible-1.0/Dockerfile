FROM lab-ub2204:1.0
LABEL maintainer="leo"

RUN apt update \
  && DEBIAN_FRONTEND=noninteractive \
  && apt install -y software-properties-common \
  && apt-add-repository -y ppa:ansible/ansible \
  && apt install -y ansible \
  && mkdir /root/.ssh && chmod 700 /root/.ssh \
  && apt autoclean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
