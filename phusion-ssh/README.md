To use phusion/baseimage for X11 Forwarding, here is what I do:

Put your SSH public key in the ssh-pub-keys folder

$ docker build -t phu .

$ docker run -d -P --name=phu1 phu

$ ssh root@$(docker inspect --format '{{ .NetworkSettings.IPAddress }}' phu1) leafpad

It should start a leafpad GUI.
