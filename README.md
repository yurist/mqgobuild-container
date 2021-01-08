A simple container to build golang applications with IBM MQ dependencies.

- Base image Dockerfile in ./mqdocker, builds an image with a complete MQ installation
- Actual image for go builds is in ./mqgo

A few points:

- Why to have a custom build MQ container if one is available from IBM? The answer is the new IBM containers have no yum installed (I have no idea why.) While it is not necessary for MQ installation proper since it's already in rpm format, but it's very hard to use that image for builds - try to install git or gcc.
- The image is based off CentOS, because MQ uses rpm images and the easiest to deal with them is on the Fedora lineage.

In order to use:

- Download IBM MQ for Linux and put the file in ./mqdocker. Adjust ./mqdocker/Dockerfile if necessary to reflect correct file name instead of mqadv_dev921_linux_x86-64.tar.gz if different.
- Download golang for Linux, put the file in ./mqgo, adjust Dockerfile there to use the correct file name instead of go1.14.13.linux-amd64.tar.gz if needed.
- Run:

docker build -t mq-docker ./mqdocker
docker build -t mqgo ./mqgo

- To use mqgo container for the build, just run it:

docker run --rm -it --name mqgo -v <location of your source code>:/usr/src/work  mqgo

When inside the container, make sure to update path to get go executalble:

export PATH=$PATH:/usr/local/go/bin

If you just need to go get, that's enough, otherwise make sure to also set GO environment variables. By default you will find the build artifacts in /root/go/bin unless you set your environment.

It's all a bit rough around the edges but it did allow me to get work done. (Had to re-build my mqlambdatm executable on an older Linux kernel than Ubuntu 20 which I have as working Linux.)

