To test X11 Forwarding, do this:

For leafpad:

    $ dock build u1
    $ dock run-leaf u1      # a Leafpad window should be displayed

or, using `docker exec`:

    $ dock build u1
    $ dock run-only u11 u1  # start leafpad (don't close this window!)
    $ dock exec-leaf u11    # another leafpad window

For firefox:

    $ dock build u2
    $ dock run-ff u2    # start Firefox

or, using `docker exec`:

    $ dock build u2
    $ dock run-only u21 u2  # will start leafpad (don't close this window!)
    $ dock exec-ff u21      # a Firefox window should be displayed

For Firefox, all the navigation data (cookies, bookmarks, etc) is saved into
the `firefox-data/` directory, and will be available the next time you start
a Firefox in a container.

Note: as an alternative, the data could also be saved in a data-only container

Note: `nsenter` does not work, but `docker exec` does, I don't know why
