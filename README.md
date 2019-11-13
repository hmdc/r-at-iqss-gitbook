# Initial page

IQSS provides Shiny application hosting to Harvard and it's affiliates. If you  have an R Shiny app you want to host with us, read on!

R Shiny application hosting is provied through [https://www.heroku.com](Heroku), a platform as a service (PaaS) for web development. IQSS has developed a [https://github.com/hmdc/heroku-docker-r](Shiny integration for Heroku), facilitating the same Git centered approach Heroku uses for web application development in NodeJS, Scala, or Java and extending it to R.

There are some differences between IQSS Shiny application hosting and what you may be used to with [https://rstudio.com/products/connect/](RStudio Connect) or [https://www.shinyapps.io/](ShinyApps), RStudio's PaaS.

The following may not be immediately helpful, but, as you progress through the tutorial, the differences highlighted below will become apparent as you encounter them while executing R Shiny deployment workflows.

## What's not supported
* You can deploy apps to ShinyApps.io or RStudio Connect directly through RStudio. At this time, you can only deploy R applications to Heroku using Git and the Heroku command line interface (cli.)
* You are, by default, limited to 512 megabytes of ram in use per app, although we are flexible and can issue memory limit increases if necessary. Most applications should strive to run under 512 MiB of ram.

## What's supported
* Unlike ShinyApps.io, you can assign a custom SSL enabled domain to you Shiny web application.
* Your Shiny app is permanently available, unlike ShinyApps.io where new instances are started on an on-demand basis.
* You can install system level libraries by adding an ```Aptfile``` to your repository.
* We support Shiny applications which operate on data classified up to Level 3, as described in [Harvard's data classification table](https://security.harvard.edu/dct).
* You can provision databases for your R Shiny application like Redis, Postgresql, and MariaDB with one click.
* We provide support for R versions 3.5.x to 3.6.x, with Microsoft R Open (Revolution R) support in the works. See [hmdc/heroku-docker-r#4](https://github.com/hmdc/heroku-docker-r/issues/4)