FROM phusion/baseimage:0.9.15

# RUN apt-get update && apt-get install -y firefox
RUN apt-get update && apt-get install -y leafpad firefox


# # To also make SSH work, so I can do more tests:
# RUN apt-get install -y xauth
# # Copy local files into the container
# COPY . /src
# # Authorize SSH public key
# # RUN mkdir /root/.ssh  # already exists
# RUN cat /src/ssh-pub-keys/*.pub > /root/.ssh/authorized_keys
# # X11 Forwarding
# # RUN echo X11Forwarding yes >> /etc/ssh/ssh_config
# RUN cat /src/sshd_config > /etc/ssh/sshd_config
#     # I got this sshd_config file from phusion/baseimage issue #105:
#     #   https://github.com/phusion/baseimage-docker/pull/105
# EXPOSE 22


# Replace 1000 with your user / group id
RUN echo 1000 > /etc/container_environment/uid
RUN echo 1000 > /etc/container_environment/gid

ENV USER developer
ENV HOME /home/developer

RUN the_user="developer" && \
    the_home="/home/$the_user" && \
    the_capital_user=$(echo $the_user | sed 's/./\U&/') && \
    echo $the_home > /etc/container_environment/HOME && \
    echo $the_user > /etc/container_environment/USER && \
    echo ":0" > /etc/container_environment/DISPLAY && \
    echo "/tmp/.Xauthority" > /etc/container_environment/XAUTHORITY && \
    echo "$the_user:x:1000:1000:$the_capital_user,,,:/$the_user:/bin/bash" >> /etc/passwd && \
    echo "$the_user:x:1000:" >> /etc/group && \
    echo "$the_user ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/$the_user && \
    chmod 0440 /etc/sudoers.d/$the_user && \
    chown 1000:1000 -R $the_home

    # mkdir -p $the_home/.mozilla/firefox && \
    # touch $the_home/.mozilla/firefox/a-file-to-change-folder-ownership && \

CMD ["/sbin/my_init"]
