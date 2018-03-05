# hb-path

Enable hashbang for interpreters which require a directory, instead of a filename, as an argument.

## Why?

My text editor lets me run scripts that start with a #! without needing to open a shell. I could not run docker builds this way, because Docker doesn't use a filename as an argument. It needs a directory name.

As a fantastic side effect, this script addresses a common concern of docker users: You can specify a default tag for builds by including it on the hashbang line and running the Dockerfile directly from your shell. See the example below.

## Usage

Dockerfile:
```
#!hb-path docker build -t mycompany/mytag:latest -f Dockerfile

FROM ubuntu:18.04
# [...]
```

## Roadmap

- [ ] Add a token that will be replaced with the full filename