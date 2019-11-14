You can use RStudio to develop your Shiny application, whether starting a new application or migrating an already existing application. Follow these tips to ensure your RStudio workflow is optimized for Shiny on Heroku.

# Creating a new project

## From GitHub
If you cloned the [heroku-docker-r-example-app](https://github.com/hmdc/heroku-docker-r-example-app) as a template, when creating a new
project in RStudio select *Version Control*

![When creating a new project, select project from version control.](../images/select-version-control.png)
![Enter the details of your Git repository](../images/clone-git-repo.png)

Click **Tools** → **Project Options** → **Packrat**. 

Make sure that the following checkboxes are all selected. This will speed up your deployment process after the initial deploy.

* ✔️ Use packrat with this project
* ✔️ Automatically snapshot local changes
* ✔️ Git ignore packrat library
* ✔️ Git ignore packrat sources

![Your Packrat options should look like this](../images/packrat-options.png)

## From scratch