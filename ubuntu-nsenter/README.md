To test X11 Forwarding, do this:

$ docker build -t ubun .

$ docker run -d -P -ti -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix --name=ubun1 ubun

$ xhost +

$ sudo nsenter --target $(docker inspect --format {{.State.Pid}} ubun1) --mount --uts --ipc --net --pid leafpad


If I don't use xhost then it does not work, and prints:

    (process:33): Gtk-WARNING **: Locale not supported by C library.
            Using the fallback 'C' locale.
    No protocol specified
    leafpad: Cannot open display: 
