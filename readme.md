# hb-helpers

This is a collection of scripts I use to simplify the build and deployment of docker based microservices.

# Install

```
git clone git@github.com:richard-fairthorne/hb-helpers.git
cd hb-helpers
./install
```

# Commands

## hb-deploy

Build dockerfile and deploy to registry. Allows you specify a default tag on the hasbang line.

```
#!hb-deploy somecompany/someproduct:sometag
FROM mybut
# [...]
```

## hb-docker

Run docker from a dockerfile, using a hashbang. Usage is roughly the same as docker, but you can omit the context argument, and the file option.

```
#!hb-docker build -t somecompany/someproduct:sometag
FROM mybut
# [...]
```
## hb-path

Enable hashbang for interpreters which require a directory, instead of a filename, as an argument.

### Why? Legacy!

note: this came first, but hb-docker is better for docker, and this script probably isn't useful for much else since most programs use a file as an argument, and the context is specified some other way. Either way, here's a fantastic history which will bore you to tears:

My text editor lets me run scripts that start with a #! without needing to open a shell. I could not run docker builds this way, because Docker doesn't use a filename as an argument. It needs a directory name.

As a fantastic side effect, this script addresses a common concern of docker users: You can specify a default tag for builds by including it on the hashbang line and running the Dockerfile directly from your shell. See the example below.

### Usage

Dockerfile:
```
#!hb-path docker build -t mycompany/mytag:latest -f Dockerfile

FROM ubuntu:18.04
# [...]
```

### Roadmap

- [ ] Add a token that will be replaced with the full filename
