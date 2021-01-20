---

copyright:
  years: 2015, 2021
lastupdated: "2021-01-20"
subcollection: cloud-foundry

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}

{{site.data.keyword.cfee_full}} is deprecated. The most recent documentation updates for {{site.data.keyword.ibmcf_notm}} can be found in the [{{site.data.keyword.ibmcf_notm}} version of this information](/docs/cloud-foundry-public?topic=cloud-foundry-public-available_versions).
{: important}

# Available versions
{: #available_versions}

{{site.data.keyword.Bluemix}} provides all [the currently available Node.js runtimes](http://nodejs.org/dist/). Of the available runtimes, {{site.data.keyword.IBM_notm}} provides specific versions that contain enhancements and bug fixes. See [Latest updates to the Node.js buildpack](/docs/cloud-foundry?topic=cloud-foundry-nodejs-latest_updates) for more information about the supported versions.
{: shortdesc}

The IBM Node.js buildpack caches the {{site.data.keyword.IBM_notm}} runtime versions. If you use {{site.data.keyword.IBM_notm}} SDK for Node.js runtime in your application, your application performs faster when you push it to {{site.data.keyword.Bluemix_notm}}.

## Specifying a version

* Use the **node** parameter in the **engines** section in the **package.json** file to specify the version of Node.js runtime that you want to run.

* If you need to specify a version of `npm` other than the version bundled with Node.js, use the `npm` parameter in the `engines` section in the `package.json` file.  

See the following example:

```
{
  "name": "myapp",
  "description": "this is my app",
  "version": "0.1",
  "engines": {
     "node": "4.2.4",
     "npm": "3.10.10"
  }
}
```
{: codeblock}

**Note:** Always specify a node version in the `package.json` file. If a version is not specified, the latest node version is used.
