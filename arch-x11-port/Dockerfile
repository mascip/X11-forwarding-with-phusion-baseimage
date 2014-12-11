# FROM base/archlinux:2014.07.03
FROM mascip/archlinux:2014.12.09

# To avoid a bug with the filesystem: https://registry.hub.docker.com/u/base/arch/
RUN sed 's/^CheckSpace/#CheckSpace/g' -i /etc/pacman.conf

# Note: the command
#   $ pacman --noconfirm -Syu
# was executed in masci/archlinux:2014.12.09

# BROWSERS
RUN pacman --noconfirm -S nvidia-libgl && \
    pacman --noconfirm -S leafpad
RUN pacman --noconfirm -S firefox
# RUN pacman --noconfirm -S chromium

# # DEBUG TOOLS
# RUN pacman --noconfirm -S vim
# RUN pacman --noconfirm -S psmisc    # killall
# RUN pacman --noconfirm -S curl

# NON-ROOT USER
# Replace you uid, gid, and username
RUN pacman --noconfirm -S sudo
RUN export uid=1000 gid=1000 && the_user="abla" && \
    the_home="/home/${the_user}" && \
    the_capital_user=$(echo $the_user | sed 's/./\U&/') && \
    mkdir -p $the_home && \
    echo "${the_user}:x:${uid}:${gid}:${the_capital_user},,,:/${the_home}:/bin/bash" >> /etc/passwd && \
    echo "${the_user}:x:${uid}:" >> /etc/group && \
    echo "${the_user} ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/${the_user} && \
    chmod 0440 /etc/sudoers.d/${the_user} && \
    chown ${the_user}:${the_user} -R ${the_home}

# Replace username and home
ENV USER abla
ENV HOME /home/abla
WORKDIR /home/abla

USER abla

# CMD /usr/bin/leafpad
CMD /usr/bin/firefox
