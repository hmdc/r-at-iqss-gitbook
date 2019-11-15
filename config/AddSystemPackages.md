# Installing additional system-level packages

The Shiny toolchain is based on Ubuntu 18.04 (bionic). You can install any ```apt``` package present in [Ubuntu's bionic repository](https://packages.ubuntu.com/).

## Example: Adding TeXlive

First, create an ```Aptfile``` in your repository. Each line of the file represents a package. You can add as many packages as you need, however, it is best practice to keep the image small.

```bash
texlive-base
```

Now, build your application as specified in [Developing locally with Docker](deploy/DevelopLocallyWithDocker.md). Texlive-base will now be installed.

## Example: Adding rJava

This is a more common requirement for R applications. Adding rJava requires not only an Aptfile, but, some R library modifications.

First, create an ```Aptfile``` in your repository and add the JRE and JDK.

```bash
default-jre
default-jdk
```

Create another file named ```onbuild``` which looks like this:

```bash
#!/bin/sh
R CMD javareconf
```

Now, install rJava to your project in R, and take a packrat snapshot.

```R
install.packages("rJava")
packrat::snapshot()
```

Now, build your application as specified in [Developing locally with Docker](deploy/DevelopLocallyWithDocker.md). rJava will now be installed and enabled for your R appication.