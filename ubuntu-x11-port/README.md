To test X11 Forwarding, do this:

$ docker build -t ubx .

$ docker run -d -P -e DISPLAY=$DISPLAY -e XAUTHORITY=/tmp/.Xauthority -v $XAUTHORITY:/tmp/.Xauthority -v /tmp/.X11-unix:/tmp/.X11-unix --name=ubx1 ubx

    => this will start leafpad (TRY without the XAUTHORITY-related arguments??)

$ docker exec ubx1 leafpad

    => this will start another leafpad window
(note: `nsenter` does not work, but `docker exec` does)
