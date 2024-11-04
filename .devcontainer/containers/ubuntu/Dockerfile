FROM ubuntu:24.04

ARG DEV_USER=ubuntu
ARG NODE_VERSION=20.17

RUN apt update -qq \
  && apt upgrade -qq -y --no-install-recommends --no-install-suggests \
  && apt -qq -y install \
  --no-install-recommends --no-install-suggests \
  git-all \
  sudo \
  bash \
  curl \
  openssh-client \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

RUN adduser $DEV_USER sudo \
  && echo "$DEV_USER ALL=(ALL) NOPASSWD: ALL" >/etc/sudoers.d/$DEV_USER \
  && chmod 0440 /etc/sudoers.d/$DEV_USER 

# install nodejs using n
RUN curl -L https://raw.githubusercontent.com/tj/n/master/bin/n -o n \
&& bash n $NODE_VERSION \
&& rm n \
&& npm install -g n \
&& npm install -g yarn \
&& yarn global add @quasar/cli