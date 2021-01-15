---

copyright:
  years: 2017, 2020
lastupdated: "2020-05-18"
subcollection: cloud-foundry

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:hide-in-docs: .hide-in-docs}
{:app_name: data-hd-keyref="app_name"}

##Disclaimer: The Cloud Foundry Enterprise Edition has been deprecated. For the most recent updates on the documentation of Cloud Foundry Public offerings please follow:  https://cloud.ibm.com/docs/cloud-foundry-public?topic=cloud-foundry-public-getting_started-dotnet

# Getting started with ASP.NET Core
{: #getting_started-dotnet}

Congratulations, you deployed a Hello World sample application on {{site.data.keyword.Bluemix}}!  To get started, follow this step-by-step guide. Or, [download the sample code](https://github.com/IBM-Cloud/get-started-aspnet-core) and explore on your own.
{: hide-in-docs}

By following this getting started tutorial, you'll set up a development environment, deploy an app locally and on {{site.data.keyword.Bluemix}}, and integrate an {{site.data.keyword.Bluemix}} database service in your app. The ASP.NET core is complied into a .dll package. You can deploy the application with the code or with the precompiled file (.DLL) of your applicattion.

## Before you begin
{: #prereqs-dotnet}

You'll need the following:
* [{{site.data.keyword.Bluemix_notm}} account](https://cloud.ibm.com/registration)
* [{{site.data.keyword.Bluemix_notm}} CLI](/docs/cli?topic=cli-getting-started)
* [Git](https://git-scm.com/downloads){: external}
* Install .NET Core SDK 3.1 from the [.NET Core downloads website](https://www.microsoft.com/net/download/core){: external}.

## Step 1: Clone the sample app
{: #clone}

First, clone the sample app GitHub repo.
  ```
git clone https://github.com/IBM-Cloud/get-started-aspnet-core
  ```
  {: codeblock}


## Step 2: Run the app locally
{: #run_locally}

1. On the command line, change the directory to where the sample app is located.

  ```
  cd get-started-aspnet-core/src/GetStartedDotnet
  ```
  {: codeblock}

1. Run the app locally by running the following commands.

  ```
dotnet restore
  ```
  {: codeblock}

  ```
dotnet run
  ```
  {: codeblock}

1. View your app at: http://localhost:5000/.

## Step 3: Prepare the app for deployment
{: #prepare-dotnet}

To deploy to {{site.data.keyword.Bluemix_notm}}, it can be helpful to set up a manifest.yml file. The manifest.yml includes basic information about your app, such as the name, how much memory to allocate for each instance and the route. We've provided a sample manifest.yml file in the `get-started-dotnet` directory.

Open the manifest.yml file, and change the `name` from `GetStartedDotnet` to your app name, <var class="keyword varname" data-hd-keyref="app_name">app_name</var>.
{: download}

  ```
 applications:
 - name: GetStartedDotnet
   random-route: true
   memory: 512M
  ```
  {: codeblock}

In this manifest.yml file, **`random-route: true`** generates a random route for your app to prevent your route from colliding with others.  If you choose to, you can replace **`random-route: true`** with **`host: myChosenHostName`**, supplying a host name of your choice.
{: tip}

## Step 4: Deploy the app
{: #deploy}

You can use the {{site.data.keyword.Bluemix_notm}} CLI to deploy apps.

1. Log in to your {{site.data.keyword.Bluemix_notm}} account, and select an API endpoint.
  ```
ibmcloud login
  ```
  {: codeblock}

  If you have a federated user ID, instead use the following command to log in with your single sign-on ID. See [Logging in with a federated ID](/docs/iam?topic=iam-federated_id) to learn more.
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

1. **Be sure you are in the main directory, `get-started-aspnet-core`, for your application**  then push your application to {{site.data.keyword.Bluemix_notm}}:
  ```
ibmcloud cf push
  ```
  {: codeblock}

  This can take a minute. If there is an error in the deployment process, you can use the command `ibmcloud cf logs <Your-App-Name> --recent` to troubleshoot.

When deployment completes, you should see a message indicating that your app is running.  View your app at the URL listed in the output of the push command.  You can also issue the following command to view your app's status and to see the URL.
  ```
ibmcloud cf apps
  ```
  {: codeblock}

You can also go to the {{site.data.keyword.Bluemix_notm}} [Resource List](https://cloud.ibm.com/resources) to view your app.

## Step 5: Add a database
{: #add_database}

Next, we'll add an {{site.data.keyword.cloudant_short_notm}} NoSQL database to this application and set up the application so that it can run locally and on {{site.data.keyword.Bluemix_notm}}.

1. In your browser, log in to {{site.data.keyword.Bluemix_notm}} and go to the Dashboard. Select **Create resource**.
1. Search for **{{site.data.keyword.cloudant_short_notm}}**, and select the service.
1. For **Available authentication methods**, select **Use both legacy credentials and IAM**. You can leave the default settings for the other fields. Click **Create** to create the service.
1. In the navigation, go to **Connections**, then click **Create connection**. Select your application, and click **Connect**.
1. Using the default values, click **Connect & restage app** to connect the database to your application. Click **Restage** when prompted.

   {{site.data.keyword.Bluemix_notm}} will restart your application and provide the database credentials to your application using the `VCAP_SERVICES` environment variable. This environment variable is available to the application only when it is running on {{site.data.keyword.Bluemix_notm}}.

Environment variables enable you to separate deployment settings from your source code. For example, instead of hardcoding a database password, you can store it in an environment variable that you reference in your source code.
{: tip}

## Step 6: Use the database locally
{: #use_database}

We're now going to update your local code to point to this database. We'll store the credentials for the services in a JSON file. This file will get used ONLY when the application is running locally. When running in {{site.data.keyword.Bluemix_notm}}, the credentials will be read from the `VCAP_SERVICES` environment variable.

1. In the `src/GetStartedDotnet` directory, create a `vcap-local.json` file.

1. Copy and paste the following JSON object into the `vcap-local.json` file, and save your changes.

   ```json
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

1. Find your app in the {{site.data.keyword.Bluemix_notm}} [Resource List](https://cloud.ibm.com/resources). On the Service Details page for your app, click **Connections** in the sidebar. Click the {{site.data.keyword.cloudant_short_notm}} menu icon (**&hellip;**) and select **View credentials**.

1. Copy and paste just the `url` value from the credentials to the `url` field of the `vcap-local.json` file, replacing `CLOUDANT_DATABASE_URL`.

1. From the `get-started-aspnet-core/src/GetStartedDotnet` directory, restart your application by running the following command.

   ```
   dotnet run
   ```
   {: codeblock}

1. Refresh your browser view at http://localhost:5000/. Any names you enter into the app will now get added to the database.

Your local app and the {{site.data.keyword.Bluemix_notm}} app share the database.  View your {{site.data.keyword.Bluemix_notm}} app at the URL listed in the output of the `ibmcloud cf push` command.  Names you add from either app should appear in both when you refresh the browsers.

Remember, if you don't need your app live, stop it so you don't incur any unexpected charges.
{: tip}

## Next Steps

* [Tutorials](/docs/tutorials/index.html)
* [Samples](https://ibm-cloud.github.io){: external}
* [Architecture Center](https://www.ibm.com/cloud/garage/category/architectures){: external}
