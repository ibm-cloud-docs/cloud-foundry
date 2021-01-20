---

copyright:
  years: 2017, 2021
lastupdated: "2021-01-20"
subcollection: cloud-foundry

---

{:new_window: target="_blank"}
{:codeblock: .codeblock}

{{site.data.keyword.cfee_full}} is deprecated. The most recent documentation updates for {{site.data.keyword.cf_notm}} can be found in the [{{site.data.keyword.cf_notm}} version of this information](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_own_jre).
{: important}

# Use your own JRE
{: #using_own_jre}

You can run your Liberty application on {{site.data.keyword.Bluemix}} with your own JRE. The liberty-for-java buildpack will provide support for the [runtimes supported by WebSphere Liberty](https://www.ibm.com/support/knowledgecenter/en/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/rwlp_restrict.html#rwlp_restrict__rest13), but cannot guarantee full functionality of unsupported versions. You must complete the following to make your JRE available for your application.
* Host the JRE in a location that the buildpack can download it from.
* Host an `index.yml` file that provides the location of the JRE.
* Configure your application to use your JRE.

## Host the JRE and `index.yml`
{: #hosting_jre}

You must host the JRE file on a web server that the liberty-for-java buildpack can download from. You can host the file on {{site.data.keyword.Bluemix_notm}} with any of the available server facilities, or you can host it in a publicly available location. The server must be configured with an `index.yml` file that specifies details about the JRE file.

Complete the following steps to host the JRE and the `index.yml` file:
  1. Acquire the JRE, which must be the version for use on a UNIX 64-bit OS, and must be a `tar.gz` file.
  2. Host the JRE file in a location from which the liberty-for-java buildpack can download it.
  3. Provide an `index.yml` file at the hosting location. The `index.yml` file must include an entry that contains a version ID of the JRE followed by a colon and the complete JRE file location URL.
    * Define the JRE version in the `index.yml` file.

    ```
    ---
    jre_version: https://hostingLocation/jreName.tar.gz
    ```
    {: codeblock}

    * Include the JRE version ID and the complete JRE file location.  For example:

    ```
    ---
    1.8.0_91: https://myHostingApp.ng.bluemix.net/jre-8u91-fcs-bin-b14-linux-x64-01_apr_2016.tar.gz
    ```
    {: codeblock}

## Configure the app
{: #configure_app}

You must set two environment variables on the Liberty application to configure the buildpack to use an alternative JRE. Set the **JBP_CONFIG_OPENJDK** to identify the location of the `index.yml` file  and set the **JVM** environment variable to *openjdk*. For more information on the format for version-value strings, see the Cloud Foundry documentation on [Version Syntax and Ordering and Wildcards ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/cloudfoundry/ibm-websphere-liberty-buildpack/blob/master/docs/util-repositories.md){: new_window}.

The value for the **JBP_CONFIG_OPENJDK** variable is the `index.yml` file location and the JRE version to choose from the index.yml file.

```
'{repository_root: "https://locationToIndexYml", version: version-value}'
```
{: codeblock}

Issue the `ibmcloud cf se myAPP` command to set the **JBP_CONFIG_OPENJDK** variable, for example:
```
ibmcloud cf se myApp JBP_CONFIG_OPENJDK '{repository_root: "https://myHostingApp.ng.bluemix.net", version: 1.8.+}'
```
{: codeblock}

The *repository_root* URL does not include `index.yml` in the URL. The *repository_root* URL points to the directory level that contains the `index.yml` file, not the file itself.

To set the JVM environment variable, issue the following command:
```
ibmcloud cf se myApp JVM 'openjdk'
```
{: codeblock}

**Note**: Restage your application after setting the environment variables for the changes to take effect.

## Confirm
{: #confirmation}

To confirm that Liberty is using the expected JRE, check the staging log. Look for a message that indicates the server downloaded the buildpack from the location indicated in the `index.yml` file. See the following snippet for an example of the log output when Liberty successfully uses the expected JRE.
```
 -----> Downloading OpenJdk 1.8.0_91 from
  https://myHostingApp.ng.bluemix.net/jre-8u91-fcs-bin-b14-linux-x64-01_apr_2016.tar.gz (6.2s)
```
{: codeblock}
