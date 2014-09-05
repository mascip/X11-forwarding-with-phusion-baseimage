FROM ubuntu:14.04
# FROM ubuntu:12.10

RUN apt-get update && apt-get install -y leafpad

# Copy local files into the container
ADD . /src

EXPOSE 22
CMD    ["/sbin/init"]
