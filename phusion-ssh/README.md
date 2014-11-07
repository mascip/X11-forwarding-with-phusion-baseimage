To use phusion/baseimage for X11 Forwarding, with SSH.

First, put your SSH public key in the ssh-pub-keys folder.
Then do this:

    $ docker build -t phu .
    $ docker run -d -P --name=phu1 phu
    $ ssh root@$(docker inspect --format '{{ .NetworkSettings.IPAddress }}' phu1) leafpad

It should start a leafpad GUI.

Firefox also works:

    $ ssh root@$(docker inspect --format '{{ .NetworkSettings.IPAddress }}' phu1) firefox

