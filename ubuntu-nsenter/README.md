To test X11 Forwarding, do this:

$ docker build -t ubun .

$ docker run -d -P -v /tmp/.X11-unix --name=ubun1 ubun

$ sudo nsenter --target $(docker inspect --format {{.State.Pid}} ubun1) --mount --uts --ipc --net --pid leafpad


Which does not work, and prints:

    (process:33): Gtk-WARNING **: Locale not supported by C library.

            Using the fallback 'C' locale.

    leafpad: Cannot open display: 


For some reason on my host machine, in /tmp/.X11-unix there is a X0 file, while there is no such file inside the container in /tmp/.X11-unix. I am wondering whether that could be a problem.

Any other idea?

