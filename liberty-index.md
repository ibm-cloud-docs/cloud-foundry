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

{{site.data.keyword.cfee_full}} is deprecated. The most recent documentation updates for {{site.data.keyword.ibmcf_notm}} can be found in the [{{site.data.keyword.ibmcf_notm}} version of this information](/docs/cloud-foundry-public?topic=cloud-foundry-public-liberty_runtime).
{: important}

# Liberty for Java
{: #liberty_runtime}

Liberty for Java applications on {{site.data.keyword.Bluemix}} are powered by the liberty-for-java buildpack. The liberty-for-java buildpack provides a complete runtime environment for running Jakarta EE, Eclipse MicroProfile, Java EE, and OSGi applications on top of WebSphere Liberty. It supports popular frameworks like Spring and includes the {{site.data.keyword.IBM_notm}} JRE. Liberty enables rapid application development that is well suited to the cloud.
{: shortdesc}

## Detection
{: #liberty-detection}
The Liberty buildpack is used when the following kinds of applications are deployed:
* [WAR files](/docs/cloud-foundry?topic=cloud-foundry-options_for_pushing#stand_alone_apps)
* [EAR files](/docs/cloud-foundry?topic=cloud-foundry-options_for_pushing#stand_alone_apps)
* [Liberty server directory](/docs/cloud-foundry?topic=cloud-foundry-options_for_pushing#server_directory)
* [Liberty packaged server](/docs/cloud-foundry?topic=cloud-foundry-options_for_pushing#packaged_server)
* [Java main](/docs/cloud-foundry?topic=cloud-foundry-options_for_pushing#java_main)
* [Distzip](https://github.com/cloudfoundry/ibm-websphere-liberty-buildpack/blob/master/docs/container-distZip.md)

## Starter application
{: #liberty-starter_application}
{{site.data.keyword.Bluemix_notm}} provides several Liberty starter applications.  The Liberty starter applications are simple Liberty apps that provide a template that you can use. You can experiment with the starter apps, and make and push changes to the {{site.data.keyword.Bluemix_notm}} environment.
