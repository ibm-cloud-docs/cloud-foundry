---

copyright:
  years: 2015, 2021
lastupdated: "2021-01-21"
subcollection: cloud-foundry

---

{:new_window: target="_blank"}
{:codeblock: .codeblock}

{{site.data.keyword.cfee_full}} is deprecated. The most recent documentation updates for {{site.data.keyword.ibmcf_notm}} can be found in the [{{site.data.keyword.ibmcf_notm}} version of this information](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_beta_features).
{: important}

# Use the beta features
{: #using_beta_features}

**Important**:  Starting with Liberty for Java buildpack v3.28, the beta runtime is no longer included.  

The Liberty beta features provide early access to new functionality and programming models that might be included in a future Liberty release. Most of the beta features can also be used in applications deployed to {{site.data.keyword.Bluemix}}.

**Important**: The beta features are for development and test purposes only and cannot be used in production. For the complete terms of use, see the [beta license agreement](http://public.dhe.ibm.com/ibmdl/export/pub/software/websphere/wasdev/downloads/wlp/beta/lafiles/en.html).

| Features |
| ------ |
| `jdbc-4.3` |
| `logstashCollector-1.1` |
| `validator-1.0` |
{: caption="Table 1. Liberty Beta features available in Liberty for Java in {{site.data.keyword.Bluemix_notm}}" caption-side="top"}

To use the Liberty beta features in {{site.data.keyword.Bluemix_notm}}, you will need to do the following:

1. [Deploy a server directory or a packaged server](/docs/cloud-foundry?topic=cloud-foundry-options_for_pushing) with one or more beta features enabled in the server.xml file as in the example that follows:

  ```
<server>
    <featureManager>
        <feature>jdbc-4.3</feature>
    </featureManager>
</server>
  ```
  {: .codeblock}

2.  Set the `IBM_LIBERTY_BETA` environment variable to `true`. This variable directs the Liberty buildpack to install and enable the beta features for your application.  For example:
  * Using the [{{site.data.keyword.Bluemix_notm}} CLI](/docs/cli?topic=cli-install-ibmcloud-cli):
    ```
    ibmcloud cf set-env <yourappname> IBM_LIBERTY_BETA true
    ```
    {: .codeblock}

  * Or, using the `manifest.yml` file:
    ```
      env:
          IBM_LIBERTY_BETA: "true"
    ```
    {: .codeblock}

3. Set the `JBP_CONFIG_LIBERTY` environment variable to `"version: +"`. This variable enables the [Liberty monthly runtime](/docs/cloud-foundry?topic=cloud-foundry-buildpack_defauts#liberty_versions), which supports beta features. For example:
  * Using the {{site.data.keyword.Bluemix_notm}} CLI tool:
    ```
    ibmcloud cf set-env <yourappname> JBP_CONFIG_LIBERTY "version: +"
    ```
    {: .codeblock}

  * Or, using the `manifest.yml` file:
    ```
      env:
          JBP_CONFIG_LIBERTY: "version: +"
    ```
    {: .codeblock}

If you are enabling the beta features on an existing application, don't forget to re-stage your application after you set the environment variables.
