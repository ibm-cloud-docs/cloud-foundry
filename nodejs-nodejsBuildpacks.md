---

copyright:
  years: 2015, 2018
lastupdated: "2018-06-27"
subcollection: "Nodejs"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}

# Node.js buildpacks

{{site.data.keyword.Bluemix}} provides multiple versions of the Node.js buildpack.
{: shortdesc}

* The {{site.data.keyword.IBM_notm}} created **sdk-for-nodejs** buildpack is the default buildpack used for Node.js applications in {{site.data.keyword.Bluemix_notm}}.
* The **nodejs_buildpack** is a community buildpack provided by the Cloud Foundry community.

The **sdk-for-nodejs** buildpack takes precedence over the **nodejs_buildpack** in {{site.data.keyword.Bluemix_notm}}. If you want to use the **nodejs_buildpack** with your application instead of the **sdk-for-nodejs** buildpack, you must specify your buildpack, for example, by using the `-b` option with the `ibmcloud cf push` command.

Typically the current **sdk-for-nodejs** buildpack and a back-level version are available.  To see all the available buildpacks us the `ibmcloud cf buildpacks` command.  For example:

```
   ibmcloud cf buildpacks
   Getting buildpacks...

   buildpack                                 position   enabled   locked   filename   

   sdk_for_nodejs                            2          true      false    buildpack_sdk-for-nodejs_v2.8-20151209-1403.zip   
   nodejs_buildpack                          5          true      false    nodejs_buildpack-cached-v1.5.0.zip   
   sdk-for-nodejs_v2_7-20151118-1003         17         true      false    buildpack_sdk-for-nodejs_v2.7-20151118-1003.zip
```
{: codeblock}
