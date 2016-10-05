# Wordpress Build Tools

[![build status](https://git.dev-digitalmobil.com/dm-wordpress/mautic-build-tools/badges/master/build.svg)](https://git.dev-digitalmobil.com/dm-wordpress/mautic-build-tools/commits/master)
[![](https://images.microbadger.com/badges/version/digitalmobil/mautic-build-tools.svg)](http://microbadger.com/images/digitalmobil/mautic-build-tools "Get your own version badge on microbadger.com")
[![](https://images.microbadger.com/badges/image/digitalmobil/mautic-build-tools.svg)](http://microbadger.com/images/digitalmobil/mautic-build-tools "Get your own image badge on microbadger.com")
[![Docker Pulls](https://img.shields.io/docker/pulls/mashape/kong.svg?maxAge=2592000)](https://hub.docker.com/r/digitalmobil/mautic-build-tools/)
[![Docker Automated buil](https://img.shields.io/docker/automated/jrottenberg/ffmpeg.svg?maxAge=2592000)](https://hub.docker.com/r/digitalmobil/mautic-build-tools/)
[![license](https://img.shields.io/github/license/mashape/apistatus.svg?maxAge=2592000)](https://github.com/digitalmobil/mautic-build-tools)


# What is this?
A docker image that contains all build tools required for building [dm-mautic](https://www.digitalmobil.com) images.

Features:
  * [composer](https://getcomposer.org)
  * Use `/data` as the working directory 
  * Executing as non-privileged user `mautic-build`
  * Preserving file permissions by adopting the `/data` dir owner's UID

# How to use this image

## Installation

```sh
docker pull digitalmobil/mautic-build-tools
```

## Usage

Simple composer call in the current directory: 

```sh
docker run --rm -v $(pwd):/data digitalmobil/mautic-build-tools composer --help
```

If working with packages installed via git ssh the local .ssh directory shall be mapped into the container: 

```sh
docker run --rm -v $(pwd):/data               \
                -v ~/.ssh:/home/mautic-build/.ssh \
                digitalmobil/mautic-build-tools composer install
```

To speed up things the local cache can be utilized as well: 

```sh
docker run --rm -v $(pwd):/data                         \
                -v ~/.ssh:/home/mautic-build/.ssh           \
                -v ~/.composer:/home/mautic-build/.composer \
                digitalmobil/mautic-build-tools composer install
```
