## Make sure you have a compatible R version installed.
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

You will need to install Docker and the Heroku CLI.