To test X11 Forwarding, do this:

$ docker build -t ubx .

$ docker run -ti --rm -e DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix ubx
