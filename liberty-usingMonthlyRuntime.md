---

copyright:
  years: 2019
lastupdated: "2019-02-01"
subcollection: cloud-foundry

---

{:new_window: target="_blank"}
{:codeblock: .codeblock}

## Disclaimer: The Cloud Foundry Enterprise Edition has been deprecated. For the most recent updates on the documentation of Cloud Foundry Public offerings please follow: https://cloud.ibm.com/docs/cloud-foundry-public?topic=cloud-foundry-public-using_monthly_runtime

# Use the monthly runtime
{: #using_monthly_runtime}

The Liberty monthly runtime provides the latest version and access to new functionality and programming models.

To use the Liberty monthly runtime in {{site.data.keyword.Bluemix_notm}}, you will need to do the following:

Set the `JBP_CONFIG_LIBERTY` environment variable to `"version: +"` and `IBM_LIBERTY_MONTHLY` environment variable to `true`. These variables enable the [Liberty monthly runtime](/docs/cloud-foundry?topic=cloud-foundry-buildpack_defauts#liberty_versions). For example:
  * Using the {{site.data.keyword.Bluemix_notm}} CLI tool:
    ```
    ibmcloud cf set-env <yourappname> JBP_CONFIG_LIBERTY "version: +"
    ibmcloud cf set-env <yourappname> IBM_LIBERTY_MONTHLY true
    ```
    {: .codeblock}

  * Or, using the `manifest.yml` file:
    ```
      env:
          JBP_CONFIG_LIBERTY: "version: +"
          IBM_LIBERTY_MONTHLY: true
    ```

    ```
      env:
          JBP_CONFIG_LIBERTY: "[version: +, app_archive: {features: [javaee-8.0]}]"
          IBM_LIBERTY_MONTHLY: true
    ```
    {: .codeblock}

If you are enabling the monthly runtime on an existing application you may need to delete and re-push your application after you set the environment variables.
