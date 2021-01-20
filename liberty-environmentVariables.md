---

copyright:
  years: 2015, 2021
lastupdated: "2021-01-20"
subcollection: cloud-foundry

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}

{{site.data.keyword.cfee_full}} is deprecated. The most recent documentation updates for {{site.data.keyword.cf_notm}} can be found in the [{{site.data.keyword.cf_notm}} version of this information](/docs/cloud-foundry-public?topic=cloud-foundry-public-environment_variables).
{: important}

# Environment variables
{: #environment_variables}

Environment variables supported by Liberty for Java.

<table>
<tr>
<th align="left">Environment Variable Name</th>
<th align="left">Description</th>
</tr>

<tr>
<td>BLUEMIX_APP_MGMT_ENABLE</td>
<td>Enable [App Management utilities](/docs/cloud-foundry?topic=cloud-foundry-app_management)</td>
</tr>

<tr>
<td>BLUEMIX_APP_MGMT_INSTALL</td>
<td>Install [App Management utilities](/docs/cloud-foundry?topic=cloud-foundry-app_management)</td>
</tr>

<tr>
<td>IBM_LIBERTY_MONTHLY</td>
<td>Enable [Liberty monthly release runtime/](/docs/cloud-foundry?topic=cloud-foundry-using_monthly_runtime)</td>
</tr>

<tr>
<td>JAVA_OPTS</td>
<td>Set [Java options](/docs/cloud-foundry?topic=cloud-foundry-customizing_jre)</td>
</tr>

<tr>
<td>JBP_CONFIG_DYNATRACEAPPMONAGENT</td>
<td>Configure the [Dynatrace agent location information](/docs/runtimes/liberty/monitoring?topic=liberty-using_dynatrace#configuring_liberty_app)</td>
</tr>

<tr>
<td>JBP_CONFIG_IBMJDK </td>
<td>Configure the [IBM JRE version](/docs/cloud-foundry?topic=cloud-foundry-customizing_jre)</td>
</tr>

<tr>
<td>JBP_CONFIG_LIBERTY</td>
<td>Configure a variety of Liberty runtime options including [features for WAR or EAR files](/docs/cloud-foundry?topic=cloud-foundry-options_for_pushing#stand_alone_apps)</td>
</tr>

<tr>
<td>JBP_CONFIG_OPENJDK</td>
<td>Configure the [OpenJDK version](/docs/cloud-foundry?topic=cloud-foundry-customizing_jre)</td>
</tr>

<tr>
<td>JBP_CONFIG_OPENJ9</td>
<td>Configure the [OpenJ9 version](/docs/cloud-foundry?topic=cloud-foundry-customizing_jre)</td>
</tr>

<tr>
<td>JBP_CONFIG_SPRINGAUTORECONFIGURATION </td>
<td>Disable the [Spring Auto-Reconfiguration framework](https://github.com/cloudfoundry/java-buildpack/blob/master/docs/framework-spring_auto_reconfiguration.md). To disable, set value to enabled: false. </td>
</tr>

<tr>
<td>JBP_LOG_LEVEL</td>
<td>Set logging level of the buildpack. Possible values: <b>DEBUG</b>, <b>INFO</b> (default), <b>WARN</b>, <b>ERROR</b>, or <b>FATAL</b></td>
</tr>

<tr>
<td>JVM</td>
<td>Select the [JRE type](/docs/cloud-foundry?topic=cloud-foundry-customizing_jre)</td>
</tr>

<tr>
<td>JVM_ARGS</td>
<td>Set the [JVM arguments](/docs/cloud-foundry?topic=cloud-foundry-customizing_jre)</td>
</tr>

<tr>
<td>LBP_SERVICE_CONFIG_xxxx</td>
<td>[Override service configuration](/docs/cloud-foundry?topic=cloud-foundry-auto_config#override_service_config)</td>
</tr>

<tr>
<td>HTTP_PROXY</td>
<td>Set proxy server information</td>
</tr>

<tr>
<td>HTTPS_PROXY</td>
<td>Set proxy server information</td>
</tr>

<tr>
<td>services_autoconfig_excludes</td>
<td>Disable service [auto-configuration.](/docs/cloud-foundry?topic=cloud-foundry-auto_config#opting_out)</td>
</tr>
</table>
{: caption="Table 1. Environment variables available for Liberty for Java" caption-side="top"}

## Disabled attributes in the Liberty for Java buildpack

There are some attributes that are automatically disabled by the Liberty buildpack, that you cannot override. The following environment variables and attributes are disabled.

### Disabled attribute table

<table>
<tr>
<th>Disabled attribute </th>
<th>Element</th>
</tr>

<tr>
<td>host</td>
<td>httpEndpoint</td>
</tr>

<tr>
<td>httpPort</td>
<td>httpEndpoint</td>
</tr>

<tr>
<td>trustHostHeaderPort</td>
<td>webContainer</td>
</tr>

<tr>
<td>andextractHostHeaderPort</td>
<td>webContainer</td>
</tr>

<tr>
<td>logDirectory</td>
<td>logging</td>
</tr>

<tr>
<td>consoleLogLevel</td>
<td>logging</td>
</tr>

<tr>
<td>enableWelcomePage</td>
<td>httpDispatcher</td>
</tr>
</table>
{: caption="Table 1. Attributes disabled by Liberty for Java" caption-side="top"}
