FROM phusion/baseimage:0.9.13
    # A version of Ubuntu, specifically built for Docker

# # Set correct environment variables.
# ENV HOME /root
# #     # I don't think I need this...

# # # Regenerate SSH host keys. baseimage-docker does not contain any, so you
# # # have to do that yourself. You may also comment out this instruction; the
# # # init system will auto-generate one during boot.
# RUN /etc/my_init.d/00_regen_ssh_host_keys.sh
#     # I don't think I need this...

# Installing the environment required: xserver, xdm, flux box, roc-filer and ssh
# RUN apt-get update && apt-get install -y openssh-server leafpad
RUN apt-get update && apt-get install -y leafpad
    # I use leafpad to test whether X11 forwarding works

# # Copy local files into the container
# ADD . /src

# # Authorize SSH public key
# # RUN mkdir /root/.ssh  # already exists
# RUN cat /src/ssh-pub-keys/*.pub > /root/.ssh/authorized_keys

# # X11 Forwarding
# # RUN echo X11Forwarding yes >> /etc/ssh/ssh_config
# RUN cat /src/sshd_config > /etc/ssh/sshd_config
#     # I got this sshd_config file from phusion/baseimage issue #105:
#     #   https://github.com/phusion/baseimage-docker/pull/105

# # # Scripts to run at container startup
# # RUN mkdir -p /etc/my_init.d
# # ADD 01-some-script.sh /etc/my_init.d/01-some-script.sh
#     # I don't need this here

# EXPOSE 22
# Use baseimage-docker's init system.
CMD ["/sbin/my_init"]
