---

copyright:
  years: 2015, 2020
lastupdated: "2020-06-18"
subcollection: cloud-foundry
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}

## Disclaimer: The Cloud Foundry Enterprise Edition has been deprecated. For the most recent updates on the documentation of Cloud Foundry Public offerings please follow: https://cloud.ibm.com/docs/cloud-foundry-public?topic=cloud-foundry-public-runtime_versions

# Runtime Versions
{: #runtime_versions}

## Supported versions
{: #supported_versions}

This buildpack supports the following versions, those marked as deprecated will be removed in a future buildpack release.  See [Microsoft's support statement for LTS and Current releases](https://www.microsoft.com/net/core/support).


### .NET SDK version

| .NET SDK version        | Default          |
|-------------------------|------------------|
| 3.1.202                 |   Yes            |
| 3.1.201                 |   No             |
| 2.1.806                 |   No             |
| 2.1.805                 |   No             |
| 2.1.701                 |   No             |
| 2.1.606                 |   No             |
| 2.1.605                 |   No             |
| 2.1.509                 |   No             |
| 2.1.508                 |   No             |
| 2.1.403                 |   No             |


### .NET Core runtime versions

| .NET Core runtime version | Release type      |
|---------------------------|-------------------|
| 3.1.4                     | Current           |
| 3.1.3                     | Normal            |
| 2.1.17                    | Normal            |



### .NET aspnetcore versions

| .NET aspnetcore version | Release type        |
|---------------------------|-------------------|
| 3.1.4                     | Current           |
| 3.1.3                     | Normal            |
| 2.1.18                    | Normal            |
| 2.1.17                    | Normal            |




## Specifying the .NET SDK version

Control the .NET SDK version with an optional `global.json` file in the application's root directory. For example:
```
   {
      "sdk": {
        "version": "3.1.202"
      }
   }
```
{: codeblock}

If not specified, the latest MSBuild tooling is used.  To use project.json tooling, you can specify one of the listed project.json versions, but keep in mind that these versions will be removed in the future.  If the specified version is not included in the buildpack, the default version is used, and a warning appears in staging logs.
