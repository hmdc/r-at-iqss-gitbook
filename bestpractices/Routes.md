# Using Routes in Shiny

In web applications, a **route** is the absolute path after the hostname.

In ```https://www.example.com/a/b/c```, the route is ```/a/b/c```.

In ```https://www.example.com/a/b```, the route is ```/a/b```.

R can display different content or widgets depending on the URL path when using the [shiny-router](https://appsilon.com/shiny-router-package/) package, installable via cran.

```R
packages.install("shiny-router")
packrat::snapshot()
```
