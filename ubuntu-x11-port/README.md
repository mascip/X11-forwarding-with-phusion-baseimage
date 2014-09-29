To test X11 Forwarding, do this:

Put your SSH public key in the ssh-pub-keys folder

$ docker build -t ubu .

$ docker run -d -P --name=ubu1 ubu

$ ssh root@$(docker inspect --format '{{ .NetworkSettings.IPAddress }}' ubu1) leafpad

This last command should start a leafpad GUI, if X11 Forwarding works properly

