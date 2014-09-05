FROM ubuntu:14.04
# FROM ubuntu:12.10

RUN apt-get update && apt-get install -y openssh-server leafpad

# Copy local files into the container
ADD . /src

# Authorize SSH public key
RUN mkdir /root/.ssh
RUN cat /src/ssh-pub-keys/*.pub > /root/.ssh/authorized_keys

# X11 Forwarding
RUN echo X11Forwarding yes >> /etc/ssh/ssh_config

# SSHD
RUN mkdir /var/run/sshd
RUN sed --in-place=.bak 's/without-password/yes/' /etc/ssh/sshd_config
    # set the PermitRootLogin  parameter in sshd_config
    # needed for 14.04. See explanation here: https://groups.google.com/forum/#!topic/docker-user/RLo12CHB6o8

EXPOSE 22
CMD    ["/usr/sbin/sshd", "-D"]
