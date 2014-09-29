To test X11 Forwarding, do this:

$ xhost +

$ docker build -t ubx .

$ docker run -ti --rm -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix ubx
