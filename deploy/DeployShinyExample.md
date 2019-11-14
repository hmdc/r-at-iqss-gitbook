By the end of this section, you will have a working Shiny app running on Heroku which looks like this:

![A working Shiny app deployed to Heroku](../images/working-app.png)

# Clone the example repository
Clone the repository from the command line and open the resultant directory: heroku-docker-r-example-app
```
git clone https://github.com/hmdc/heroku-docker-r-example-app.git
cd heroku-docker-r-example-app
```
You can also ```git clone``` using the repository's SSH url if you have your
SSH keys configured in GitHub. This is the preferred way, but, it is un-necessary.
```
git clone git@github.com:hmdc/heroku-docker-r-example-app.git
cd heroku-docker-r-example-app
```
# Login to Heroku on the command line
Run ```heroku login```. This will open a browser window. Make sure to click *Login via SSO* entering g-harvard as the SSO name, as shown in the screenshots below.

# Deploy the application to Heroku
You are now logged into Heroku via the CLI and can deploy the Shiny application you just cloned locally to Heroku.

## Create/modiy the application; set the stack to container
You may have been assigned an empty, undeployed application name by the IQSS operations team. Think of this as an empty container you will be deploying the example app to. If you have been assigned an application name, keep it handy. Alternatively, you may have permissions to **create** applications in Heroku.
For the purposes of this tutorial, the application name will be referenced by ```$APPLICATION```. If you've been assigned an application name, replace ```$APPLICATION``` in all examples with your application name. Otherwise, just make one up. All application names in Heroku are globally unique like domain names, so, choose an application name that will most likely be available. You can always try again if your first choice is unavailable.

### If you have application creation permissions..
This command will create an application called ```$APPLICATION``` in the g-harvard team, using the container stack. Our IQSS Shiny framework is built upon the Docker container framework, so any application on Heroku which will run R Shiny code must be configured to use the container stack.

```heroku create --stack=container $APPLICATION --team=g-harvard```

### If you have an application name already assigned..
```heroku stack:set container -a $APPLICATION --team=g-harvard```

## Set the Heroku git remote
You will use Git to deploy this application to Heroku. Heroku provides an additional **git remote** that when pushed to will automatically build and release your application. From the ```heroku-docker-r-example-app``` directory, run
```
heroku git:remote -a $APPLICATION
```
This will create a new git remote. Check it out, run
```
$ git remote
heroku
origin
```
Origin is GitHub, in this case, whereas Heroku represents the Heroku remote.

## Deploy
Run ```git push heroku``` 

## Wait...
You'll see a lot of logs. Heroku is building and packaging ```heroku-docker-r-example-app```. Following successful deployment, which may take
up to twenty minutes, you'll be returned an URL for your app.

You can actually press Ctrl+C and detach from the deployment process and it will continue deploying. No need to keep watch, although it is useful. At any time,
you can view the build logs for $APPLICATION by running

```
heroku logs -a $APPLICATION
```

You can also follow the log so any log updates are printed to the console.

```
heroku logs -a $APPLICATION -t
```

There are ways to speed up deployments explored in [Speeding up deployments](deploy/SpeedingUp.md). These steps are unnecessary, but, very hepful.

## View your application
Click the link returned in the log output. If you see the R Shiny app pictured above, it worked! Keep reading to learn how to deploy **your own Shiny** app, whether you're building an entirely new app or migrating an application previously running on ShinyApps.io, RStudio Connect, or locally.