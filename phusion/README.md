Trying to use phusion/baseimage for X11 Forwarding, but it does not work.

Here is what I do:

Put your SSH public key in the ssh-pub-keys folder

$ docker build -t phu .

$ docker run -d -P --name=phu1 phu

$ ssh root@$(docker inspect --format '{{ .NetworkSettings.IPAddress }}' phu1) leafpad

Instead of starting a leafpad GUI, it says:
    X11 forwarding request failed on channel 0
    leafpad: Cannot open display: 

How can I get it to work...?
