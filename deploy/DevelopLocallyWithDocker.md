# Develop locally with Docker

Using Docker to run your R Shiny app locally will produce a running instance of your application which mirrors Heroku 1:1. While testing your application within RStudio should work in most cases, running your application with Docker can provide additional verification for any code changes you've made.

Haven't yet installed Docker? Read [Setup your environment](SetupEnvironment.md) before continuing.

All the following exercises use [heroku-docker-r-example-app](https://github.com/hmdc/heroku-docker-r-example-app) as the example application. To test your own application, substitute ```heroku-docker-r-example-app``` with your own application checkout or directory.

## Building your application docker image

The following command will compile your application into a docker image tagged with the name *my-local-heroku-docker-r-example-app*. You will see the same build output as you would if you pushed your code to the git Heroku remote.

```
cd heroku-docker-r-example-app
docker build -t my-local-heroku-docker-r-example-app .
```

## Running your application docker image
Once completed, you can run the docker image you produced:

```
docker run -p 8080:8080 -e PORT=8080 my-local-heroku-docker-r-example-app:latest
```

This will run your Shiny application on port 8080. You may need to click *Allow* on any security-related popups, common to Windows and Mac OS X, which ask whether you want to allow Docker to bind to port 8080. 

If you're already using port 8080 or want to use a different port, substitute 8080 throughout the entire command with a different port number, except for ports 12000 to 13000 which are reserved for R threads within the container.

```
docker run -p 11000:11000 -e PORT=11000 my-local-heroku-docker-r-example-app:latest
```

## Viewing in the browser

Go to [http://localhost:8080](http://localhost:8080) and you should see your application.
