# Setting up a custom domain for your Shiny app

{% hint style="tip" %}
Before you can setup an SSL certificate and custom domain for your Shiny app, you must have deployed your application first.
{% endhint %}

Ready to assign a custom domain for your Shiny app? 

We can offer ```*.hmdc.harvard.edu``` subdomains or you can bring your own. 
If you would like an HMDC sub-domain, please e-mail [support@help.hmdc.harvard.edu](mailto:support@help.hmdc.harvard.edu?subject=I%20need%20a%20hmdc%20subdomain%20for%20my%20heroku%20app) after completing the following instructions.

## Enabling automatic or manual SSL certificate management

In the Heroku dashboard, go to your app and click on the *Settings* tab, pictured below using ```my-docker-r-example-app``` as an example.

![Select Settings tab on your application in Heroku](../images/settings-for-app-on-heroku.png)

Scroll down and click on *Configure SSL*.

![Click the Configure SSL button](../images/configure-ssl.png)

Select *Automatic* if you're not bringing your own custom SSL certificates, or *Manually* if you are. Continue through the screens as shown below until you're brought back to the settings page.

![Select automatic or manual. You most likely want to select Automatic.](../images/ssl-automatic-or-manual.png)

Now, you're ready to configure your custom domain.

## Configuring your custom domain

## Adding a DNS CNAME entry
