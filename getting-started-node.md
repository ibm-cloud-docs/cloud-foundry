---

copyright:
  years: 2017, 2021
lastupdated: "2019-11-07"
subcollection: cloud-foundry
---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:hide-in-docs: .hide-in-docs}
{:hide-dashboard: .hide-dashboard}
{:app_name: data-hd-keyref="app_name"}

{{site.data.keyword.cfee_full}} is deprecated. The most recent documentation updates for {{site.data.keyword.cf_notm}} can be found in the [{{site.data.keyword.cf_notm}} version of this information](/docs/cloud-foundry-public?topic=cloud-foundry-public-getting-started-node).
{: important}

# Getting started with SDK for Node.js
{: #getting-started-node}

<!-- This file is reused in the CF Public subcollection. -->

Congratulations, you deployed a Hello World sample application on {{site.data.keyword.Bluemix}}!  To get started, follow this step-by-step guide. Or, [download the sample code](https://github.com/IBM-Cloud/get-started-node) and explore on your own.
{: hide-in-docs}

By following this tutorial, you'll set up a development environment, deploy an app locally on {{site.data.keyword.Bluemix}}, and integrate an {{site.data.keyword.Bluemix_notm}} database service in your app.

Throughout these docs, references to the Cloud Foundry CLI are now updated to the {{site.data.keyword.Bluemix_notm}} CLI! The {{site.data.keyword.Bluemix_notm}} CLI has the same familiar Cloud Foundry commands, but with better integration with {{site.data.keyword.Bluemix_notm}} accounts and other services. Learn more about getting started with the {{site.data.keyword.Bluemix_notm}} CLI in this tutorial.
{: tip}

## Before you begin
{: #prereqs-node}

You'll need the following accounts and tools:

* [{{site.data.keyword.Bluemix_notm}} account](https://cloud.ibm.com/registration)
* [{{site.data.keyword.Bluemix_notm}} CLI](/docs/cli/reference/ibmcloud?topic=cloud-cli-install-ibmcloud-cli)
* [Git](https://git-scm.com/downloads){: external}
* [Node](https://nodejs.org/en/){: external}


## Step 1: Clone the sample app
{: #clone-node}

First, clone the Node.js *hello world* sample app GitHub repo.
  ```
git clone https://github.com/IBM-Cloud/get-started-node
  ```
  {: codeblock}

## Step 2: Run the app locally
{: #run_locally-node}

Use the npm package manager to install dependencies and run your app.

1. On the command line, change the directory to where the sample app is located.
  ```
cd get-started-node
  ```
  {: codeblock}

1. Install the dependencies listed in the [package.json ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://docs.npmjs.com/files/package.json){: new_window} file to run the app locally.  
  ```
npm install
  ```
  {: codeblock}

1. Run the app.
  ```
npm start  
  ```
  {: codeblock}

1. View your app at the following URL: http://localhost:3000

Use [nodemon ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://nodemon.io/){: new_window} for automatic restarting of application on file changes.
{: tip}

## Step 3: Prepare the app for deployment
{: #prepare-node}

To deploy to {{site.data.keyword.Bluemix_notm}}, it can be helpful to set up a manifest.yml file. The manifest.yml includes basic information about your app, such as the name, how much memory to allocate for each instance and the route. We've provided a sample manifest.yml file in the `get-started-node` directory.

Open the manifest.yml file, and change the `name` from `GetStartedNode` to your app name, <var class="keyword varname" data-hd-keyref="app_name">app_name</var>.
{: download}

```
applications:
- name: GetStartedNode
  random-route: true
  memory: 128M
```
{: codeblock}

In this manifest.yml file, **random-route: true** generates a random route for your app to prevent your route from colliding with others.  If you choose to, you can replace **random-route: true** with **host: myChosenHostName**, supplying a host name of your choice.
{: tip}

## Step 4: Deploy the app
{: #deploy-node}

You can use the {{site.data.keyword.Bluemix_notm}} CLI to deploy apps to {{site.data.keyword.Bluemix_notm}}.

1. Log in to your {{site.data.keyword.Bluemix_notm}} account, and select an API endpoint.
  ```
ibmcloud login
  ```
  {: codeblock}

  If you have a federated user ID, instead use the following command to log in with your single sign-on ID. See [Logging in with a federated ID](/docs/iam?topic=iam-federated_id) for more information.
  ```
ibmcloud login --sso
  ```
  {: codeblock}

1. Target a Cloud Foundry org and space:

  ```	  
ibmcloud target --cf
  ```
  {: codeblock}

  If you don't have an org or a space set up, see [Adding orgs and spaces](/docs/account?topic=account-orgsspacesusers).
    {: tip}

1. From within the *get-started-node* directory, push your app to {{site.data.keyword.Bluemix_notm}}.

  ```
ibmcloud cf push
  ```
  {: codeblock}

Deploying your application can take a few minutes. When deployment completes, you'll see a message that your app is running. View your app at the URL listed in the output of the push command, or view both the app deployment status and the URL by running the following command:

  ```
ibmcloud cf apps
  ```
  {: codeblock}

You can also go to the {{site.data.keyword.Bluemix_notm}} [resource list ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/resources){: new_window} to view your app.

You can troubleshoot errors in the deployment process by using the `ibmcloud cf logs <Your-App-Name> --recent` command.
{: tip}

## Step 5: Add a database
{: #add_database-node}

Next, we'll add an {{site.data.keyword.cloudant_short_notm}} NoSQL database to this application and set up the application so that it can run locally and on {{site.data.keyword.Bluemix_notm}}.

1. In your browser, log in to {{site.data.keyword.Bluemix_notm}} and go to the Dashboard. Select **Create resource**.
1. Search for **{{site.data.keyword.cloudant_short_notm}}**, and select the service.
1. For **Available authentication methods**, select **Use both legacy credentials and IAM**. You can leave the default settings for the other fields. Click **Create** to create the service.
1. In the navigation, go to **Connections**, then click **Create connection**. Select your application, and click **Connect**.
1. Using the default values, click **Connect & restage app** to connect the database to your application. Click **Restage** when prompted.

   {{site.data.keyword.Bluemix_notm}} will restart your application and provide the database credentials to your application using the `VCAP_SERVICES` environment variable. This environment variable is available to the application only when it is running on {{site.data.keyword.Bluemix_notm}}.

Environment variables enable you to separate deployment settings from your source code. For example, instead of hardcoding a database password, you can store it in an environment variable that you reference in your source code.
{: tip}

## Step 6: Use the database
{: #use_database-node}

We're now going to update your local code to point to this database. We'll create a JSON file that will store the credentials for the services the application will use. This file will get used ONLY when the application is running locally. When running in {{site.data.keyword.Bluemix_notm}}, the credentials will be read from the `VCAP_SERVICES` environment variable.

1. In the `get-started-node` directory, create a file called `vcap-local.json` with the following content:
  ```
  {
    "services": {
      "cloudantNoSQLDB": [
        {
          "credentials": {
            "url":"CLOUDANT_DATABASE_URL"
          },
          "label": "cloudantNoSQLDB"
        }
      ]
    }
  }
  ```
  {: codeblock}

2. Find your app in the {{site.data.keyword.Bluemix_notm}} [resource list ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/resources){: new_window}. On the Service Details page for your app, click **Connections** in the sidebar. Click the {{site.data.keyword.cloudant_short_notm}} menu icon (**&hellip;**) and select **View credentials**.

3. Copy and paste just the `url` from the credentials to the `url` field of the `vcap-local.json` file, replacing `CLOUDANT_DATABASE_URL`.

4. Run your application locally.
  ```
npm start  
  ```
  {: codeblock}

  View your local app at http://localhost:3000. Any names you enter into the app will now get added to the database.

**Avoid trouble**: {{site.data.keyword.Bluemix_notm}} defines the PORT environment variable when your app runs on the cloud. When you run your app locally, the PORT variable is not defined, so 3000 is used as the port number. See [Run your app locally](/docs/cloud-foundry?topic=cloud-foundry-hints) for more information.

  Your local app and the {{site.data.keyword.Bluemix_notm}} app are sharing the database. Names you add from either app will appear in both when you refresh the browsers.

Remember, if you don't need your app live on {{site.data.keyword.Bluemix_notm}}, stop the app so you don't incur any unexpected charges.
{: tip}

## Next steps
{: #nextsteps-node}

[Manage your Node.js app](/docs/cloud-foundry?topic=cloud-foundry-nodejs_runtime). Some example tasks include configuring caching and integrating third-party services.
{: hide-dashboard}

Check out the following resources:
{: hide-dashboard}

* [Tutorials](/docs/tutorials?topic=solution-tutorials-tutorials)
* [Samples ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm-cloud.github.io){: new_window}
* [Architecture Center ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud/garage/category/architectures){: new_window}
