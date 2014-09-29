FROM ubuntu:14.04

# IMPORTANT: I must run
#     $ xhost +
# on the host, in order to get X11 forwarding

RUN apt-get update && apt-get install -y leafpad

CMD    ["/sbin/init"]
