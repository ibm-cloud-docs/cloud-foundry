---

copyright:
  years: 2015, 2021
lastupdated: "2021-01-20"
subcollection: cloud-foundry

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:important: .important}

{{site.data.keyword.cfee_full}} is deprecated. The most recent documentation updates for {{site.data.keyword.ibmcf_notm}} can be found in the [{{site.data.keyword.ibmcf_notm}} version of this information](/docs/cloud-foundry-public?topic=cloud-foundry-public-buildpack_defauts).
{: important}

# Liberty for Java buildpack defaults
{: #buildpack_defauts}

The Liberty buildpack is updated frequently in {{site.data.keyword.Bluemix}}. Each release might contain security fixes or feature enhancements.

The buildpack has default values for settings such as the Java version or Liberty feature set for WAR or EAR applications. Some of the default values might change between the buildpack release, which might adversely impact the application. To prevent the application from being affected by the change in buildpack defaults, take steps to configure your application to avoid relying on the buildpack defaults.

## Liberty versions
{: #liberty_versions}

The buildpack provides two versions of the Liberty runtime:
1. A long-term stable release
  * It is the default Liberty runtime.
  * It does not provide any [beta features](/docs/cloud-foundry?topic=cloud-foundry-using_beta_features).
  * Typically updated on a quarterly basis.

2. The monthly release
  * It must be explicity enabled by setting the **JBP_CONFIG_LIBERTY** environment variable with the **"version: +"** value and
  the **IBM_LIBERTY_MONTHLY** environment variable with **true**.
  * It provides [monthly features](/docs/cloud-foundry?topic=cloud-foundry-using_monthly_runtime).
  * Typically updated every 4 weeks.

## Liberty features
{: #default_liberty_features}

When you deploy WAR or EAR files, the buildpack provides a configuration for the application with a default set of Liberty features. Although rare, that default set of Liberty features might change between the buildpack releases. The change in the default feature set might adversely affect the application. There are options to ensure that the application is not affected by the change in the feature defaults.

* Set the JBP_CONFIG_LIBERTY environment variable to explicitly specify a list of enabled features for the application. For more information, see [Stand-alone Applications](/docs/cloud-foundry?topic=cloud-foundry-options_for_pushing#stand_alone_apps).
* Deploy your application as a [server directory](/docs/cloud-foundry?topic=cloud-foundry-options_for_pushing#server_directory) or a [packaged server](/docs/cloud-foundry?topic=cloud-foundry-options_for_pushing#packaged_server). Provide a custom server.xml file that specifies the exact set of features that are needed by your application.

Applications that are deployed as a server directory or a packaged server are unaffected by the change in the Liberty features default.

## Java version
{: #java_version}

The buildpack provides a default JRE for the application. The major or minor version of the JRE might change between the buildpack releases. The minor version of the JRE might be updated frequently while the major version is rarely updated. The change in the major version of the JRE might adversely affect the application.

To ensure that the application is not affected by the major version change, set the environment variable with the appropriate JRE version as described in [Customizing the JRE](/docs/cloud-foundry?topic=cloud-foundry-customizing_jre). For best results, adopt Java 8 for your applications.
