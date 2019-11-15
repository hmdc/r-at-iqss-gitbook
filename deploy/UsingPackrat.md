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

In the R console, run

```R
R version 3.6.1 (2019-07-05) -- "Action of the Toes"
Copyright (C) 2019 The R Foundation for Statistical Computing
Platform: x86_64-apple-darwin15.6.0 (64-bit)

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

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
```

After your project's dependencies are installed, run the following from the same R console

```R
packrat::snapshot()
```

to save your project's dependencies to the file ```packrat/packrat.lock```
