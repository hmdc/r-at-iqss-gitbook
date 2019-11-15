# File Storage

{% hint style="danger" %}
Never commit very large files to your Git repository. This will slow down all deployments and, depending on the size of the file, may make your project undeployable.
{% endhint %}

Your Shiny application may use large CSVs, JPEGs, PNGs, etc. Large binaries or large CSVs should be stored in Amazon S3 or in a database.

Heroku allows you to provision **addons** for your app, including databases like PostgreSQL or S3 buckets for asset storage.

Explore the [add-ons Heroku offers](https://elements.heroku.com/addons).

For storing images, we suggest using [Bucketeer](https://elements.heroku.com/addons/bucketeer).

Most add-ons when provisioned add environment variables to your Shiny application which contain the credentials and paths to access these add-ons.

Please start with the lowest tier of each add-on you're using. If you need a larger database, S3 bucket, or other add-on, reach out to support to discuss your options. E-mail [support@help.hmdc.harvard.edu](mailto:support@help.hmdc.harvard.edu?subject=I%20want%20to%20discuss%20Heroku%20addons).