FROM lab-ub2204:1.0
LABEL maintainer="leo"

RUN apt update \
  && DEBIAN_FRONTEND=noninteractive \
  && apt install -y curl \
  && curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py \
  && python3 get-pip.py \
  && python3 -m pip install ansible-core==2.13.0 \
  && mkdir /root/.ssh && chmod 700 /root/.ssh \
  && apt autoclean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
