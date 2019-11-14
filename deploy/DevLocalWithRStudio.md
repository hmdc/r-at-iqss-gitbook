You can use RStudio to develop your Shiny application, whether starting a new application or migrating an already existing application. Follow these tips to ensure your RStudio workflow is optimized for Shiny on Heroku.

# Creating a new project

## From GitHub
If you cloned the [heroku-docker-r-example-app](https://github.com/hmdc/heroku-docker-r-example-app) as a template, when creating a new
project in RStudio select *Version Control*

![When creating a new project, select project from version control.](../images/select-version-control.png)
![Enter the details of your Git repository](../images/clone-git-repo.png)

## Enable Packrat
Click **Tools** → **Project Options** → **Packrat**. 

Make sure that the following checkboxes are all selected. This will speed up your deployment process after the initial deploy.

* ✔️ Use packrat with this project
* ✔️ Automatically snapshot local changes
* ✔️ Git ignore packrat library
* ✔️ Git ignore packrat sources

![Your Packrat options should look like this](../images/packrat-options.png)

## From scratch

When creating a project from scratch in RStudio, make sure the following options are selected.

* ✔️ Create a git repository
* ✔️ Use packrat with this project

![Your project options should look like this](../images/project-options.png)

# Migrating an existing project

Open your project normally as you would through RStudio and enable Packrat, following the above instructions for enabling Packrat support in a project.
