# Configuring Shiny session auto-reconnect

You may have noticed that your application greys out after a short period of time. This is by design - as R is single threaded and uses a persistent websocket to communicate with the R process, the developers of the R programming language wanted to limit resource consumption by severing the connections of idle users.

## Using allowReconnect

Adding this inside your server function will allow auto-reconnect:

```R
server = function(input, output, session) {
   ...
   session$allowReconnect("force")
}
```

Your R session will still disconnect after idling, but, will reconnect in 5 seconds. This is our prefferred method because it will still utilize Heroku's load balancing functionality if one of your dynos is under heavy use.