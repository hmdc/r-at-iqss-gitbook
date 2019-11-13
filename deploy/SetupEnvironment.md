# Install a compatible R version installed.
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
This step is optional, but, *highly reccomended*. While you don't need Docker to deploy your Shiny applications to Heroku or develop them locally, using Docker you'll be able
to view your application locally just as it will appear in production. With Docker, you can confirm that code which works locally in your development environment will work in Heroku.

You can download Docker for Windows, OS X, or Linux.

# Install Heroku
You will need the Heroku CLI in order to properly configure and deploy your R Shiny application. 

Follow the [Heroku CLI installation instructions](https://devcenter.heroku.com/articles/heroku-cli#download-and-install).

Now, you'll deploy the Shiny example application to Heroku.