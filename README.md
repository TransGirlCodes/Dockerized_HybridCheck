Dockerized HybridCheck R package
================================

<div align="center">
<a href="http://ward9250.github.io/HybridCheck">
<img src="http://ward9250.github.io/HybridCheck/img/HybridCheckLogo.png" height="250" alt="HybridCheck Logo Here"></img>
</a>
</div>

This is the Dockerized R bundled with the R package [HybridCheck](http://ward9250.github.io/HybridCheck/index.html) and its
dependencies.

The image is available from
[Docker Hub](https://registry.hub.docker.com/u/ward9250/hybridcheck/).

## Usage:

### Basic use:

To use this container you will need Docker installed on your computer.

To run R with HybridCheck on your computer in a terminal:

```sh
docker run -it ward9250/hybridcheck
```

### Mounting directories with data:

You will probably want to mount your current working directory (i.e. the one
with the data files you want to analyze with HybridCheck) so as the Docker
container can 'see' the directory and your files.

```sh
docker run -ti --rm -v "$PWD":/home/docker/mydatafiles -w /home/docker/mydatafiles -u docker r-base
```

### Running your analysis using your own Dockerfile:

As an alternative to the command for running the Docker container with a mounted
working directory (above), you can collect the scripts and data needed to run
your analysis, into a folder with your own Dockerfile for your analysis/project.
The Dockerfile you put in this directory should specify ward9250/hybridcheck in
the FROM line. An example Dockerfile which does this is below:

```sh
FROM ward9250/hybridcheck:latest
COPY . /home/docker/myanalysis
WORKDIR /home/docker/myanalysis
CMD ["Rscript", "myscript.R"]
```

Once you have made your Dockerfile and have it in the directory along with your
R script and data-files, you can build it and then run your analysis,
by executing the following command from your projects folder:

```sh
docker build -t myproject .
```

Then you can run the Docker container of your analysis you just built:

```sh
docker run myproject
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
