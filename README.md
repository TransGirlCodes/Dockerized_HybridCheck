Dockerized HybridCheck Shiny App
================================

This is the Dockerized R bundled with the R package [HybridCheck](http://ward9250.github.io/HybridCheck/index.html) and its
dependencies.

The image is available from
[Docker Hub](https://registry.hub.docker.com/u/ward9250/hybridcheck/).

## Usage:

To use this container you will need Docker installed on your computer.

To run R with HybridCheck on your computer in a terminal:

```sh
docker run -it ward9250/hybridcheck
```

## Intended purpose:

This container was created to avoid issues installing and running the R package
'HybridCheck'. Common issues installing and running these include
different versions of R or R packages, non-standard R library locations and so
on.

If you learn Docker enough to use it to download and run containers, you avoid
all these possible pitfalls, as everything needed to get the package running is
provided for in this container, which will run on any system Docker is
available for, which certainly covers Windows, OS X, and the popular GNU/Linux
distros.
