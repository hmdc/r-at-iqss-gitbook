# Configuration

You can easily customize your R Shiny app deployment if necessary. You can:

* Set up a custom domain for your Shiny application, using Heroku to automatically generatie LetsEncrypt SSL certificates or by bringing your own.

* Configure the level of parallelism for your Shiny app - by default your Shiny app will consume the amount of CPUs available to the dyno divided by 2. If your application uses *a lot of memory* this may be a necessary step.

* Install system-level packages: The IQSS Shiny toolchain allows you to install system level packages, like Java or ImageMagick. If you use ```rJava```, don't skip this chapter!
