# Limiting the number of R threads

R is single threaded, meaning that R can only execute one instruction at a time. This makes developing web applications in R which users expect to be highly performant hard. Long running computations will prevent multiple users from viewing your site concurrently.

There are a few design suggestions explored in [Best Practices](bestpractices/README.md) that can make a large impact, however, the IQSS Shiny toolchain enables basic concurrency for your Shiny applications through the use of load balancing.

The Shiny IQSS toolchain launches as many R processes as there are CPUs, divided by two. Shiny by itself takes up around 60 to 100MiB of memory without performing any work, so using a 1:1 mapping of R process to CPU would most likely result in an out of memory error in most cases.

If your application uses a lot of memory, the default of ```CPUs / 2``` may still result in out of memory errors. You can manually set the number of R processes to launch by adding the environment variable ```R_NUM_PROCS``` to your Heroku depoyment.

## Using only 1 R process.

Open the settings tab of your Shiny app on Heroku and click **Reveal Config Vars**.

In KEY, enter ```R_NUM_PROCS```.

In VALUE, enter 1.

Then, click **ADD**

Click more and select **Restart all dynos**. This is disruptive - if you only have one dyno, user connections will be severed. When your application is restarted, it will only launch 1 R process.