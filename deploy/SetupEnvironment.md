# Install Git
There are multiple Git clients available. Install one or install many.
Listed below are some of our top picks.

- [Windows](https://git-scm.com/download/win)
- [Mac](https://git-scm.com/download/mac)

If you're using Linux, install Git through your distribution's package
manager. For example, ```apt-get -y install git``` or ```yum -y install git```.

Read [Getting Started - Installing Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) for more information.

Note that all the examples in this tutorial will be using Git *on the command line*. You will use ```command.exe``` or powershell (your choice) in Windows, Terminal in OS X, or any terminal emulator in Linux.

# Ensure a compatible version of R is installed.
You should have R and optionally RStudio installed. Shiny at IQSS
supports R 3.5.x to 3.6.x. If you're using R < 3.5.x, upgrade now
as there is no guarantee that code built for R < 3.5.x will function
when deployed to the Heroku environment.

{% hint style="info" %}
You can find out the version of R you have installed through RStudio.
Enter the following into the R Console.
```
> R.version.string
[1] "R version 3.6.1 (2019-07-05)"
```
{% endhint %}

# Install Docker
This step is optional, but, *highly reccomended*. While you don't need Docker to deploy your Shiny applications to Heroku or develop applications locally, using Docker you'll be able run your Shiny application with the exact same tooling and libraries as in production.

You can download Docker for Windows, OS X, or Linux. 
- [Mac](https://docs.docker.com/docker-for-mac/install/)
- [Windows](https://docs.docker.com/docker-for-windows/install/)

Alternatively, if using OS X, you can use [brew](https://brew.sh/) to install docker.

```brew cask install docker```

# Install Heroku
You will need the Heroku CLI in order to properly configure and deploy your R Shiny application. 

Follow the [Heroku CLI installation instructions](https://devcenter.heroku.com/articles/heroku-cli#download-and-install).

Now, you'll deploy the Shiny example application to Heroku.