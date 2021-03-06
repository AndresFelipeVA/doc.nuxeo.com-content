---
title: Docker Image
review:
  date: '2021-01-11'
  status: ok
labels:
  - multiexcerpt
  - multiexcerpt-include
toc: true
description: Discover how to install the Nuxeo Platform with the Docker image.
tree_item_index: 250
---

## Requirements

The only requirement to run the Nuxeo Docker image is [Docker](https://docs.docker.com/get-docker/) itself.

Java, as well as all the external software, are integrated in the Docker image.

## What's in the Nuxeo Image

The Nuxeo Docker image is described by this [Dockerfile](https://github.com/nuxeo/nuxeo/blob/master/docker/Dockerfile).

Based on CentOS 7, it includes:

- Azul's [Zulu OpenJDK 11](https://www.azul.com/downloads/zulu-community/?version=java-11-lts&package=jdk).
- A bare Nuxeo server without any package installed.
- Some basic Open Source converters, e.g.: ImageMagick, LibreOffice.
- A `nuxeo` user with the `900` fixed UID.
- The directories required to have the Nuxeo configuration, data and logs outside of the server directory, with appropriate permissions.
- An entrypoint script to configure the server.
- The default recommended volumes.
- The environment variables required by the server, typically `NUXEO_HOME` and `NUXEO_CONF`.
- The exposed port `8080`.

## Running the Image

Currently, the image is hosted in our public [Docker registry](https://packages.nuxeo.com/#browse/search/docker).

To pull the latest tag of the `nuxeo/nuxeo` image from the Docker registry and run a container from it, run:

```shell
docker run --name nuxeo -p 8080:8080 docker.packages.nuxeo.com/nuxeo/nuxeo
```

The `latest` tag points to the latest release, for instance [11.4](https://github.com/nuxeo/nuxeo/releases/tag/v11.4).

To get the latest build, versioned `11.x.y`, you can use the `11.x` tag.

The default command executed when running a container is `nuxeoctl console`. It can be overridden by specifying an argument to `docker run`. For instance, to open a bash shell in the container and automatically remove the container when it exits, just run:

```shell
docker run -it --rm docker.packages.nuxeo.com/nuxeo/nuxeo bash
```

For a production setup and general best practices, please read about [Mounting Data, Log and Temporary Directories as Volumes]({{page page='setup-best-practices'}}#mounting-data-log-and-temporary-directories-as-volumes).

## Configuring the Image at Runtime

Though we encourage to have immutable images configured at build time, in some cases it makes sense to configure a container at runtime. This typically applies to the address and credentials of each back-end store (database, Elasticsearch, S3, etc.) that are specific to a given deployment: development, staging, production, etc.

### Configuration Properties

To add or update some configuration properties when running a container from a Nuxeo image, please read the related section about [nuxeo.conf]({{page page='configuration-parameters-index-nuxeoconf'}}#docker-image).

### Environment Variables

Currently, these are the environment variables that are taken into account by a Nuxeo image:

- `JAVA_OPTS`
- `NUXEO_CLID`
- `NUXEO_CONNECT_URL`
- `NUXEO_PACKAGES`

#### JAVA_OPTS

Please first have a look at the default [JVM settings]({{page page='setup-best-practices'}}#container-environment) in the Nuxeo Docker image.

The value of `JAVA_OPTS` is appended to the `JAVA_OPTS` property defined in `nuxeo.conf` at startup.

For instance, to make the Nuxeo Launcher display the JVM settings in the console, run:

```shell
docker run --name nuxeo \
  -p 8080:8080 \
  -e JAVA_OPTS=-XshowSettings:vm \
  docker.packages.nuxeo.com/nuxeo/nuxeo
```

#### NUXEO_CLID

The value of `NUXEO_CLID` is copied to `/var/lib/nuxeo/instance.clid` at startup.

For instance, to run a container with a registered Nuxeo instance:

```shell
docker run --name nuxeo \
  -p 8080:8080 \
  -e NUXEO_CLID=<NUXEO_CLID> \
  docker.packages.nuxeo.com/nuxeo/nuxeo
```

#### NUXEO_CONNECT_URL

`NUXEO_CONNECT_URL` allows to override the default Connect URL at startup.

For instance, to run a container with another Connect URL than the default one:

```shell
docker run --name nuxeo \
  -p 8080:8080 \
  -e NUXEO_CONNECT_URL=<NUXEO_CONNECT_URL> \
  docker.packages.nuxeo.com/nuxeo/nuxeo
```

#### NUXEO_PACKAGES

`NUXEO_PACKAGES` allows to define a space separated list of Nuxeo packages to install at startup.

For instance, to run a container with the `nuxeo-web-ui` and `nuxeo-drive` packages installed:

```shell
docker run --name nuxeo \
  -p 8080:8080 \
  -e NUXEO_CLID=<NUXEO_CLID> \
  -e NUXEO_PACKAGES="nuxeo-web-ui nuxeo-drive" \
  docker.packages.nuxeo.com/nuxeo/nuxeo
```

### Shell Scripts

To run some shell scripts when starting a container from a Nuxeo image, you can add
`*.sh` files in the `/docker-entrypoint-initnuxeo.d` directory of the image.

They will be alphabetically sorted and executed at the very end of the `ENTRYPOINT`, after handling the environment variables. Thus, if you run a container by passing the `NUXEO_CLID` environment variable, invoking `nuxeoctl` in such a shell script will work as being registered.
