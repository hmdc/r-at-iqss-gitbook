# Resolving Application Error screen

When trying to access your Shiny application, do you see the screen below?

![An application crash](../images/app-crash.png)

If so, something is wrong with your application. The most common culprits are listed below in order of their likeliness:

* You ran out of system memory.

* You're installing a package from GitHub rather than CRAN.

* You're using ```packages.install()``` outside of ```init.R```, in your R server function.

* A required R library has a system-level dependency that isn't articulated in your Aptfile.

* You're trying to install ```rJava``` without installing a JDK.

How can you determine which of the above (or, if you're lucky - an entirely different problem) is responsible for your application crash? Read on!
