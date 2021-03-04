# Initial page

{% hint style="danger" %}
IQSS no longer provides this service. Documentation remains for reference only.
{% endhint %}

R Shiny application hosting is provided through [Heroku](https://www.heroku.com), a platform as a service (PaaS) for web development. IQSS has developed a [Shiny integration for Heroku](https://github.com/hmdc/heroku-docker-r), extending the same Git centered approach Heroku uses for web application development in NodeJS, Scala, or Java to R.

There are some differences between IQSS Shiny application hosting and what you may be used to with [RStudio Connect](https://rstudio.com/products/connect/) or [ShinyApps.io](https://www.shinyapps.io/), RStudio's PaaS.

The following may not be immediately helpful, but, as you progress through the tutorial, the differences highlighted below will become apparent as you encounter them while executing R Shiny deployment workflows.

## What's not supported

* You can deploy apps to ShinyApps.io or RStudio Connect directly through RStudio. At this time, you can only deploy R applications to Heroku using Git and the Heroku command line interface (cli.)
* You are, by default, limited to 512 megabytes of ram in use per app, although we are flexible and can issue memory limit increases if necessary. Most applications should strive to run under 512 MiB of ram.
* We do not provide any data storage for your application's static assets -- images, CSV(s), or data files. However, you can easily provision an [S3 bucket](https://elements.heroku.com/addons/bucketeer) through Heroku to house such files.

## What's supported

* You can assign a custom SSL enabled domain to your Shiny web application.
* Your Shiny app is always available.
* You can install system level libraries by adding an ```Aptfile``` to your repository and specifying which [Ubuntu 18.04](https://packages.ubuntu.com) compatible packages to install. The CRAN [bionic-cran35](https://cran.r-project.org/bin/linux/ubuntu/) apt repository is pre-installed. 
* You can provision databases for your R Shiny application like Redis, Postgresql, and MariaDB with one click.
* We provide support for R versions 3.5.x to 3.6.x, with Microsoft R Open (Revolution R) support in the works. See [hmdc/heroku-docker-r#4](https://github.com/hmdc/heroku-docker-r/issues/4) for more details.
