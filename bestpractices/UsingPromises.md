# Using Promises

As explained in [Limiting the number of R Threads](../config/NumRThreads.md), R is single-threaded, unless it's not.

While our Shiny toolchain optimizes your application by running multiple R processes, using promises will maximize your performance far greater than balancing between multiple R processes.

## What is asynchronous programming?

Synchronus programming progresses linearly through code executions. The following reads a CSV from the included URL.

```R
value <- read.csv("http://example.com/data/data.csv")
a <- 1+2
```

Before ```a``` can be assigned the value of ```3```, R will execute an HTTP request to ```http://example.com/data/data.csv```, download the CSV, and store it in the variable ```value```. The R process is blocked until this is completed. There is no reason to wait for the CSV to complete downloading before continuing with the rest of your application's code, in particular because network functions can be offloaded to the operating system's event handler (libuv). 

```R
promise <- future(read.csv("http://example.com/data/data.csv"))
a <- 1+2
```

The above will download the CSV in a non-blocking manner, meaning that ```a``` will be assigned 3 even if ```read.csv``` hasn't completed yet.

Asynchronous programming will execute an instruction, designated as asynchronous by the ```promise``` keyword, in a different thread, without waiting for it's result. You can offload long-running operations to a subsidiary R thread spawned by the promise library.

## Asynchronous R documentation

If you're processing CSVs, executing long-running code in your R Shiny app, you **should** use promises to speed up your application.

The following tutorials detail how to develop asynchronous R application.

* [Working with promises in R](https://rstudio.github.io/promises/articles/overview.html)

* [Async programming in R and Shiny](https://medium.com/@joe.cheng/async-programming-in-r-and-shiny-ebe8c5010790)

* [How to use the new R promises package](https://appsilon.com/an-example-of-how-to-use-the-new-r-promises-package/?nabe=4634331497365504:0&utm_referrer=https%3A%2F%2Fwww.google.com%2F)
