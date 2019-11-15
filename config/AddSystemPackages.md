# Installing additional system-level packages

The Shiny toolchain is based on Ubuntu 18.04 (bionic). You can install any ```apt``` package present in [Ubuntu's bionic repository](https://packages.ubuntu.com/).

## Example: Adding TeXlive

First, create an ```Aptfile``` in your repository. Each line of the file represents a package. You can add as many packages as you need, however, it is best practice to keep the image small.

```bash
texlive-base
```

Now, build your application as specified in [Developing locally with Docker](deploy/DevelopLocallyWithDocker.md). Texlive-base will now be installed.

## Example: Adding rJava

This is a more common requirement for R applications. As rJava requires some additional configuration commands, we'll be using ```onbuild``` rather than Aptfile which runs arbitrary commands.

Create a file named ```onbuild``` which looks like this:

```bash
#!/bin/bash
# install java jdk
apt-get update -q
apt-get install -qy --no-install-recommends openjdk-8-jdk openjdk-8-jre
rm -rf /var/lib/apt/lists/*

# configure R for Java
R CMD javareconf &> /dev/null
```

Install rJava to your project in R, and take a packrat snapshot.

```R
install.packages("rJava")
packrat::snapshot()
```

Build your application as specified in [Developing locally with Docker](deploy/DevelopLocallyWithDocker.md). rJava will now be installed and enabled for your R appication.

You can always deploy immediately to Heroku which would build your application and produce the same results, but, testing locally first is always preferred.
