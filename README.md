Trying to make X11 Forwarding work in phusion/baseimage, and using [nsenter](https://github.com/jpetazzo/nsenter) rather than SSH. To build something like [docker-desktop](https://github.com/rogaha/docker-desktop).

In each folder, the README tells you how to test X11 Forwarding (with 3 or 4 shell commands)

In the **ubuntu-ssh/** folder you will find how to make X11 Forwarding work (through SSH) in the ubuntu:14.04 image.

In the **phusion/** folder, you will find how to make the same thing work in phusion/baseimage.

In the **ubuntu-nsenter** folder, I use nsenter instead of SSH.

In the **ubuntu-x11-port** folder, I run the program directly with the CMD command in the Dockerfile

In the **phusion-nsenter** folder, I use nsenter with a phusion-baseimage image.
