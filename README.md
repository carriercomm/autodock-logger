autodock-logger
===============

[![Image Layers](https://badge.imagelayers.io/prologic/autodock-logger:latest.svg)](https://imagelayers.io/?images=prologic/autodock-logger:latest)

Logger plugin for autodock.

autodock-logger is MIT licensed.

> **note**
>
> See: [autodock](https://github.com/prologic/autodock)

Basic Usage
-----------

Start the daemon:

    $ docker run -d -v /var/run/docker.sock:/var/run/docker.sock --name autodock prologic/autodock

Link and start an autodock plugin:

    $ docker run -i -t --link autodock prologic/autodock-logger

Now whenever you start a new container autodock will listen for Docker events. The `autodock-logger` plugin will log all Docker Events received by autodock.

`docker-compose.yml`:

``` sourceCode
autodock:
    image: prologic/autodock
    ports:
        - "1338:1338/udp"
        - "1338:1338/tcp"
    volumes:
        - /var/run/docker.sock:/var/run/docker.sock

autodocklogger:
    image: prologic/autodock-logger
    links:
        - autodock
```
