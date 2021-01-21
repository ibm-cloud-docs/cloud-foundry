---

copyright:
  years: 2018, 2021
lastupdated: "2021-01-20"
subcollection: cloud-foundry

---

{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:tip: .tip}
{:important: .important}

{{site.data.keyword.cfee_full}} is deprecated. The most recent documentation updates for {{site.data.keyword.ibmcf_notm}} can be found in the [{{site.data.keyword.ibmcf_notm}} version of this information](/docs/cloud-foundry-public?topic=cloud-foundry-public-install-features).
{: important}

# Install Liberty features
{: #install-features}

The Liberty for Java runtime includes [a subset of features](/docs/cloud-foundry?topic=cloud-foundry-liberty_features#liberty_features) that are available in Liberty. You can install features that are not included in the runtime by running the Liberty `installUtility` command as a Cloud Foundry pre-runtime hook when the application is pushed to {{site.data.keyword.cloud_notm}}.

For a full list of available features, see [Liberty features ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/rwlp_feat.html).

For information on using pre-runtime hooks, see [Configure Pre-Runtime Hooks ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://docs.cloudfoundry.org/devguide/deploy-apps/deploy-app.html#profile) in the Cloud Foundry documentation.

1. In the root directory of the application that you want to push to {{site.data.keyword.cloud_notm}}, create a `.profile.d` directory.

1. In the `.profile.d` directory, create a script file that runs the `installUtility` command as shown in the following example.

   This example installs the `audit-1.0` feature.

   ```
   #!/bin/sh
   echo "Installing audit-1.0"
   export PATH=$PATH:$HOME/app/.java/jre/bin

   $HOME/app/.liberty/bin/installUtility install audit-1.0 --acceptLicense
   ```
   {: codeblock}

   You can install multiple features by specifying additional features names separated by spaces.
   {: tip}

1. Push your app to {{site.data.keyword.cloud_notm}}, using the `-p` parameter to specify the application's root directory.

   For example, run the following command to push your app:
   ```
   ibmcloud cf push myApp -p /<path-to-application>
   ```
   {: codeblock}

1. Verify that the feature installed successfully by viewing the application's recent log.

   For example, run the following command to display the log:
   ```
   ibmcloud cf logs myApp --recent
   ```
   {: codeblock}

    If the feature was installed, the output shows the following messages:

    ```
    2018-09-18T13:01:17.61-0400 [APP/PROC/WEB/0] OUT Installing audit-1.0
    2018-09-18T13:01:19.13-0400 [APP/PROC/WEB/0] OUT Establishing a connection to the configured repositories ...
    2018-09-18T13:01:19.13-0400 [APP/PROC/WEB/0] OUT This process might take several minutes to complete.
    2018-09-18T13:01:21.28-0400 [APP/PROC/WEB/0] OUT Successfully connected to all configured repositories.
    2018-09-18T13:01:21.28-0400 [APP/PROC/WEB/0] OUT Preparing assets for installation. This process might take several minutes to complete.
    2018-09-18T13:01:25.87-0400 [APP/PROC/WEB/0] OUT The --acceptLicense argument was found. This indicates that you have
    2018-09-18T13:01:25.87-0400 [APP/PROC/WEB/0] OUT accepted the terms of the license agreement.
    ```
