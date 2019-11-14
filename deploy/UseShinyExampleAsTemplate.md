You've deployed the previous example and want to start building an R Shiny application from scratch or migrate a pre-existing app. The easiest way
to do either is to clone [heroku-docker-r-example-app](https://github.com/hmdc/heroku-docker-r-example-app) as a template.

# Starting an app from scratch

If you're starting to develop a R Shiny app from scratch -- this process is easy.
Login to GitHub, go to [heroku-docker-r-example-app](https://github.com/hmdc/heroku-docker-r-example-app), and click the _Use this template_ button.

This will create a new repository based of `heroku-docker-r-example-app`. You can clone this new repository and use it as a base for your R Shiny application.

You can now begin development using the IDE of your choice.

# Integrating a pre-existing R Shiny application

Go to [heroku-docker-r-example-app](https://github.com/hmdc/heroku-docker-r-example-app) and generate a new repository using _Use this template_.

Migrating a pre-existing R Shiny application requires a few more steps. The following workflow is our preferred and supported method, but, for the adventurous, all you need is the `Dockerfile`, `heroku.yml` and `run.R` files from the repository. 

{% hint style="warning" %}
You *must* have run.R present in any Shiny project for it to run on Heroku
{% endhint %}

Clone the newly created repository and add your pre-existing code.

# Selecting the version of R to use
The [heroku-docker-r-example-app](https://github.com/hmdc/heroku-docker-r-example-app) template defaults to using R 3.6.1.

The [Dockerfile](https://github.com/hmdc/heroku-docker-r-example-app/blob/master/Dockerfile) determines which version of R is used for your code in Heroku.

```
FROM hmdc/heroku-docker-r:3.6.1-shiny
```

If you use a diferent version of R, replace 3.6.1 with the desired version of R.
At present, we support R 3.5.x to 3.6.1.

If you want to use R 3.5.1, your Dockerfile should look like

```
FROM hmdc/heroku-docker-r:3.5.1-shiny
```

# Caveats

If you're familar with [Packrat](https://rstudio.github.io/packrat/) and use it, you're in good shape. If not, Packrat is a R library dependency management tool which
automatically downloads and builds all libraries required for your application. The
R Shiny IQSS toolchain automatically installs Packrat when you deploy your application. No additional steps are necessary. 

However, in order for your application to work properly in Heroku, you must ensure that:

1. You do not use ```install.packages()``` anywhere in your code. This will cause R to install packages during application runtime, rather than before the application is launched. There is one exception to this rule when installing libraries from GitHub, explained in #3.

2. All your R libraries required with ```library()``` exist in [CRAN](https://cran.r-project.org/web/packages/). 

3. If you're installing custom R packages from GitHub using the ```devtools``` library, add an ```init.R``` file to your repository and move these installation functions to ```init.R```. All instructions in this file will be executed during the build process, before your application goes live.

