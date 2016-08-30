# particle-docker-dev-env

A Dockerised build environment for [Particle](https://particle.io/) devices.

## Contents

* Ubuntu base image
* GCC C and C++ compilers
* CMake
* Git
* `xxd`
* GDB
* Node.js
* cppcheck

## Usage
Typical usage would resemble something like this:

	docker run -it --rm \
	    --volume $(pwd):/source \
	    --volume $HOME/.particle:/root/.particle \
	    --workdir /source \
	    charleskorn/particle-docker-dev-env:latest \
	    YOUR COMMAND HERE

This:

* starts a temporary container that will be cleaned up when the command terminates (`--rm`)
* asks for STDIN to be attached (`-i`), and for a pseudo-TTY to be allocated (`-t`)
* mounts the current directory into the container at `/source`
* mounts your Particle CLI settings directory into the container (so your login persists between containers)
* changes the initial working directory to `/source`
* runs `YOUR COMMAND HERE` in the container and then terminates
