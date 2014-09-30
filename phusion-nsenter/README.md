To test X11 Forwarding, do this:

$ docker build -t phu .

$ docker run -d -P -ti -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix --name=phu1 phu

$ xhost +

$ sudo nsenter --target $(docker inspect --format {{.State.Pid}} phu1) --mount --uts --ipc --net --pid leafpad

It should start a leafpad GUI.


If I don't use xhost then it does not work, and prints:

    (process:33): Gtk-WARNING **: Locale not supported by C library.
            Using the fallback 'C' locale.
    No protocol specified
    leafpad: Cannot open display:
    Trying to use phusion/baseimage for X11 Forwarding

