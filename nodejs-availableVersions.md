---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-20"
subcollection: cloud-foundry

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}

## Disclaimer: The Cloud Foundry Enterprise Edition has been deprecated. For the most recent updates on the documentation of Cloud Foundry Public offerings please follow: https://cloud.ibm.com/docs/cloud-foundry-public?topic=cloud-foundry-public-available_versions

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
