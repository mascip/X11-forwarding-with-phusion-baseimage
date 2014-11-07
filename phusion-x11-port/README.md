For this attempt to do X11 Forwarding on phusion-baseimage, you MUST have Docker > 1.3, to use the `docker exec` command.

If it's not available for your distribution yet, then you can [use the Binaries](http://docs.docker.com/installation/binaries/).
Before trying any command, you MUST indicate where your Docker Binaries are, in the `$my_docker_cmd` variable in the file called `dock` (line 2). If you are not using the Binaries (because you have Docker 1.3 installed already), then you can just put "docker" in this variable.

Once this in done, these commands will let you run Leafpad from within a phusion-baseimage container:

    $ ./dock build px1
    $ ./dock run-only px11 px1
    $ ./dock exec-setuser-leaf px11 &

The commands that will be run behind the scene, are these (they will get printed in your terminal) :

    $ docker build -t px1 .
    $ docker run \
        -d -P \
        -e DISPLAY \
        -e XAUTHORITY=/tmp/.Xauthority \
        -v /home/user/.Xauthority:/tmp/.Xauthority \
        -v /tmp/.X11-unix:/tmp/.X11-unix \
        --name=px11 px1
    $ docker exec pxb1 setuser developer leafpad &

I tried other ways to try and run Leafpad, but they don't work:

    $ ./dock build phx1
    $   ./dock run-leaf px1
    $ ./dock run-only px11 px1
    $    ./dock nsenter-leaf px11
    $    ./dock exec-leaf px11

I don't understand why, but I need to use phusion-baseimage's `setuser` to make it work:

    $ ./dock exec-setuser-leaf px11
    EXECUTING: "docker exec px11 setuser developer leafpad &"

**WORKS**, while

    $ ./dock exec-leaf px11
    EXECUTING: "docker exec px11 leafpad &"

**DOES NOT WORK**.



To run **Firefox**, I'm unsuccessful so far. My current attempt is:

    $ ./dock build phx2
    $ ./dock run-for-ff phx21 phx2
    $ ./dock exec-ff phx21

and the result is Firefox giving me this error:

    Your Firefox profile cannot be loaded. It may be missing or inaccessible.

I seem to have a problem with users and permissions...

I have started to investigate [here](https://github.com/phusion/baseimage-docker/issues/163)
