# Dockerfile for building Ansible image for Ubuntu 16.04 (xenial), with as few additional software as possible.
#
# @see https://launchpad.net/~ansible/+archive/ubuntu/ansible
#
# Version  1.0
#


# pull base image
FROM ubuntu:16.04

MAINTAINER William Yeh <william.pjyeh@gmail.com>

# It seems Xenial already includes an updated version of Ansible (2.0.0). We can add the PPA when it starts supporting Xenial
RUN \
    DEBIAN_FRONTEND=noninteractive  apt-get    update  && \
    \
    \
    echo "===> Installing Ansible..."  && \
    DEBIAN_FRONTEND=noninteractive  apt-get install -y ansible  && \
    \
    \
    echo "===> Removing APT stuff ..."  && \
    apt-get autoremove --purge -y && \
    apt-get autoclean -y          && \
    rm -rf \
      "${HOME}/.cache" \
      /var/lib/apt/lists/*  && \
    \
    \
    echo "===> Adding hosts for convenience..."  && \
    echo 'localhost' > /etc/ansible/hosts


# default command: display Ansible version
CMD [ "ansible-playbook", "--version" ]
