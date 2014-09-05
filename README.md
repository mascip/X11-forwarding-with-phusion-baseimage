Trying to make X11 Forwarding work in phusion/baseimage, and using [nsenter](https://github.com/jpetazzo/nsenter) rather than SSH.

In the **ubuntu-ssh/** folder you will find how to make X11 Forwarding work (through SSH) in the ubuntu:14.04 image.

In the **phusion/** folder, you will find how to make the same thing work in phusion/baseimage.

In the **ubuntu-nsenter** folder, you will find my (currently failed) attempt to do X11 Forwarding through nsenter.

In each folder, the README tells you how to test X11 Forwarding (with 3 shell commands)

Ultimately, my goal is to build something like [docker-desktop](https://github.com/rogaha/docker-desktop) on phusion/baseimage, and using nsenter.

