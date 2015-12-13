# BungeeCord

* * *


## About this image

This Docker image allows you to run a BungeeCord instance quickly, with minimal fuss.

This image was based on the `dlord/spigot` Docker Image.


## Base Docker image

* java:7


## How to use this image

### Starting an instance

    docker run \
        --name spigot-instance \
        -p 0.0.0.0:25577:25577 \
        -d \
        -it \
        dlord/bungeecord

### Environment Variables

The image uses environment variables to configure the JVM settings.

#### BUNGEECORD_OPTS

You may adjust the JVM settings via the `BUNGEECORD_OPTS` variable.


## Extending this image

This image is meant to be extended for packaging custom maps, plugins, and
configurations as Docker images. For server owners, this is the best way to
roll out configuration changes and updates to your servers.

If you wish to do so, here are some of the things you will need to know:

### ONBUILD Trigger

This Docker image contains one `ONBUILD` trigger, which copies any local files
to `/usr/src/bungeecord`.

When a container is started for the first time, the contents of this folder is
copied to `BUNGEECORD_HOME` via `rsync`, except for anything that starts with
`world`. It will also ensure that the `BUNGEECORD_HOME/plugins` folder exists,
and it will clean out any plugin jar files to make way for new ones. This is
the simplest way to roll out updates without going inside the data volume.

### JVM Arguments

You can include them via the `BUNGEECORD_OPTS` variable in your Dockerfile.


## Supported Docker versions

This image has been tested on Docker version 1.9


## Feedback and Contributions

Feel free to open a [Github issue][].

If you wish to contribute, you may open a pull request. I am very strict with
commit standards, and pull requests with no descriptions will be closed
immediately.

For commit standards, I follow a similar style to the Linux Kernel. See section
1.2 of the [How to Get Your Change Into the Linux Kernel][]. For examples and
tips, check out [this guide by Chris Beams][].

[Github issue]: https://github.com/dlord/spigot-bungeecord-docker
[Minecraft EULA]: https://account.mojang.com/documents/minecraft_eula
[How to Get Your Change Into the Linux Kernel]: https://www.kernel.org/doc/Documentation/SubmittingPatches
[this guide by Chris Beams]: http://chris.beams.io/posts/git-commit/
