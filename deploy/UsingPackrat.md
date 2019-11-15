# Speeding up deployments with Packrat

Earlier, you configured Packrat support in RStudio. If you use RStudio as your primary IDE, you'll now be benefitting from Packrat's dependency management. If you aren't using RStudio or aren't yet using Packrat, you're still using Packrat.

The IQSS Shiny toolchain installs Packrat during the build process and determines your dependencies automatically, without any intervention, but this makes the build process *very long*. Every time you build your application in Docker or Heroku, instead of using a stored, cached set of dependencies, the Shiny toolchain re-creates the ```packrat.lock``` file, requiring every dependency to be re-compiled and re-installed.

## Installing Packrat into an R project outside of RStudio

All instructions below are  summarized from [RStudio's official Packrat documentation](https://rstudio.github.io/packrat/).

Open your project's directory, and execute R.

```bash
cd heroku-docker-r-example-app
R
```

In the R console, run the following:

```R
> install.packages("packrat")
trying URL 'http://cran.cnr.berkeley.edu/bin/macosx/el-capitan/contrib/3.6/packrat_0.5.0.tgz'
Content type 'application/x-gzip' length 456629 bytes (445 KB)
==================================================
downloaded 445 KB


The downloaded binary packages are in
        /var/folders/nh/xkzmf2xj70q2v5_gjvf0kyz00000gn/T//Rtmp3svuh7/downloaded_packages
> packrat::init()
Initializing packrat project in directory:
- "~/projects/heroku-docker-r-example-app"

Adding these packages to packrat:
                _
    BH            1.69.0-1
    R6            2.4.1
    Rcpp          1.0.3
    assertthat    0.2.1
    backports     1.1.5
    ...
    ...

Initialization complete!
Packrat mode on. Using library in directory:
- "~/projects/heroku-docker-r-example-app/packrat/lib"

```

After your project's dependencies are installed, your project's dependencies will be saved to the file ```packrat/packrat.lock```

## Installing new packages to the Packrat bundle

During the course of application development, you may need to add new libraries.
If you want to install a library and use it in your application, first, run R
and install the library per usual, then create a new packrat snapshot. This will update ```packrat/packrat.lock``` with the new library.

Perform the same process if upgrading a package.

```R
> library(packrat)
> install.packages("ggplot2")
> packrat::snapshot()
```

## Restoring installed packages

If you've downloaded your project onto a completely new machine, you can restore all the required dependencies by open your project's directory, executing R and running:

```R
install.packages("packrat")
library(packrat)
packrat::restore()
```

The ```install.packages("packrat")``` is optional if Packrat is already installed.

## Using .gitignore
You *must* have a proper .gitignore file within your project. Packrat downloads tarballs (compressed folders) of all your required libraries and places them in the ```packrat``` sub-directory of your project, check it out:

```bash
bash-3.2$ find  packrat/lib/x86_64-apple-darwin15.6.0/3.6.1 -type d -maxdepth 1
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/packrat
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/glue
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/pkgconfig
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/htmltools
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/jsonlite
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/plogr
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/utf8
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/shiny
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/rlang
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/vctrs
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/digest
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/tibble
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/magrittr
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/crayon
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/tidyselect
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/zeallot
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/cli
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/promises
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/R6
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/pillar
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/xtable
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/assertthat
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/backports
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/fastmap
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/httpuv
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/BH
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/purrr
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/mime
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/later
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/dplyr
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/sourcetools
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/ellipsis
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/fansi
packrat/lib/x86_64-apple-darwin15.6.0/3.6.1/Rcpp
```

None of this should be committed or pushed to GitHub as our Shiny toolchain will look at ```packrat.lock``` and download, install, and clean up all your required libraries upon deploy.

Make sure you have a .gitignore in your repsitory that looks like this

```bash
.Rproj.user
.Rhistory
.RData
.Ruserdata
packrat/lib*
packrat/src
```