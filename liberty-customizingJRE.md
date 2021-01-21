---

copyright:
  years: 2015, 2021
lastupdated: "2021-01-20"
subcollection: cloud-foundry

---

{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:important: .important}

{{site.data.keyword.cfee_full}} is deprecated. The most recent documentation updates for {{site.data.keyword.ibmcf_notm}} can be found in the [{{site.data.keyword.ibmcf_notm}} version of this information](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre).
{: important}

# Customize the JRE
{: #customizing_jre}

Applications run in a Java runtime environment (JRE) that is provided and configured by the Liberty buildpack. The Liberty buildpack also makes it possible to configure the JRE version or type, customize the JVM options, or overlay the JRE functions.

## {{site.data.keyword.IBM_notm}} JRE

By default, applications are configured to run with a lightweight version of the {{site.data.keyword.IBM}} JRE. This lightweight JRE is stripped down to provide core, essential function with a much reduced disk and memory footprint. For more information about the contents of the lightweight JRE, see [Small Footprint JRE](http://www.ibm.com/support/knowledgecenter/SSYKE2_8.0.0/com.ibm.java.lnx.80.doc/user/small_jre.html).

 {{site.data.keyword.IBM_notm}}JRE version 8 is used by default.  The Liberty buildpack also includes the latest OpenJ9 11 JRE as an alternate JRE.  
 Use the JBP_CONFIG_IBMJDK environment variable to specify an alternative JRE. For example, to use the latest OpenJ9 JRE provided by the Liberty buildpack set the following environment variable:
```
    ibmcloud cf set-env myapp JBP_CONFIG_IBMJDK "version: 11.+"
```
{: codeblock}

The version property can be set to a version range. There are two supported version ranges: 1.8.+ and 11.+. For best results, use Java 8.

## OpenJDK
{: #openjdk}

Optionally, applications can be configured to run with OpenJDK as the JRE. To enable an application to run with OpenJDK set the JVM environment variable to "openjdk". For example, using the {{site.data.keyword.Bluemix_notm}} command line tool, run the command:
```
    ibmcloud cf set-env myapp JVM 'openjdk'
```
{: codeblock}

If enabled, OpenJDK version 8 is used by default. Use the JBP_CONFIG_OPENJDK environment variable to specify an alternative version of OpenJDK. For example, to use the latest OpenJDK 7, set the following environment variable:
```
    ibmcloud cf set-env myapp JBP_CONFIG_OPENJDK "version: 1.7.+"
```
{: codeblock}

The version property can be set to a version range such as 1.7.+, 1.8.+ or any specific version listed on the [list of available OpenJDK versions](https://download.run.pivotal.io/openjdk/lucid/x86_64/index.yml). For best results, use Java 8.

## OpenJ9
{: #openj9}

Optionally, applications can be configured to run with OpenJ9 as the JRE or JDK. To enable an application to run with OpenJ9 set the JVM environment variable to "openj9". For example, using the {{site.data.keyword.Bluemix_notm}} command line tool, run the command:
```
    ibmcloud cf set-env myapp JVM 'openj9'
```
{: codeblock}

If enabled, OpenJ9 version 11 is used by default. Use the JBP_CONFIG_OPENJ9 environment variable to specify an alternative version of OpenJ9. For example, to use the latest OpenJ9 8, set the following environment variable:
```
    ibmcloud cf set-env myapp JBP_CONFIG_OPENJ9 "version: 8.+"
```
{: codeblock}

If enabled, the OpenJ9 JRE is used by default. Use the JBP_CONFIG_OPENJ9 environment variable to use the JDK version of OpenJ9. For example, to use the OpenJ9 JDK, set the following environment variable:
```
    ibmcloud cf set-env myapp JBP_CONFIG_OPENJ9 "type: jdk"
```
{: codeblock}

## Oracle JRE
{: #oracle_jre}

See [Using your own JRE](/docs/cloud-foundry?topic=cloud-foundry-using_own_jre) for information on using the Oracle JRE.

## Configuring the JRE options
{: #configuring_jre}

### JVM default configuration
{: #jvm_default_config}

The Liberty buildpack configures the default JVM options by taking into account:

* An application's memory limit.  The applied JVM heap settings are calculated based on:
  * an application's memory limit, as explained in [Memory limits and the Liberty buildpack](/docs/cloud-foundry?topic=cloud-foundry-memory_limits)
  * the JRE type, as the heap-related options for the JVM vary according to the JRE's supported options.

* The [Liberty features supported in {{site.data.keyword.Bluemix_notm}}](/docs/cloud-foundry?topic=cloud-foundry-liberty_features).
  * Two-phase commit global database transactions are unsupported in {{site.data.keyword.Bluemix_notm}} and therefore disabled by setting -Dcom.ibm.tx.jta.disable2PC=true.

* The {{site.data.keyword.Bluemix_notm}} environment.

    The JVM options are configured to provide optimization in a {{site.data.keyword.Bluemix_notm}} environment and to aide diagnostics of memory-related error conditions.
  * fast failure and recovery of an application is configured by disabling JVM dumps options and killing of the processes when an application's memory is exhausted.
  * virtualization tuning ({{site.data.keyword.IBM_notm}} JRE only).
  * routing of information on the application's available memory resources at the time of failure to the Loggregator.
  * if an application is configured to enable JVM memory dumps, the killing of Java processes is disabled, and JVM memory dumps are routed to a common application "dumps" directory. These dumps can then be viewed from the {{site.data.keyword.Bluemix_notm}} dashboard or the {{site.data.keyword.Bluemix_notm}} CLI.

The following is an example default JVM configuration that is generated by the buildpack for an application that is deployed with a 512M Memory Limit:

```
    -Xtune:virtualized
    -Xmx384M
    -Xdump:none
    -Xdump:heap:defaults:file=../../../../../dumps/heapdump.%Y%m%d.%H%M%S.%pid.%seq.phd
    -Xdump:java:defaults:file=../../../../../dumps/javacore.%Y%m%d.%H%M%S.%pid.%seq.txt
    -Xdump:snap:defaults:file=../../../../../dumps/Snap.%Y%m%d.%H%M%S.%pid.%seq.trc
    -Xdump:tool:events=systhrow,filter=java/lang/OutOfMemoryError,request=serial+exclusive,exec=../../../../.buildpack-diagnostics/killjava.sh
    -Dcom.ibm.tx.jta.disable2PC=true
```
{: codeblock}

### Customizing the JVM configuration
{: #customizing_jvm}

Applications can customize the JVM options with the specifications that are defined by the JRE configured for the application. Reference the guidelines on how to specify an option and its usage directly from the JRE's documentation, as the options vary according to the JRE.

<table>
<tr>
<th align="left">JRE</th>
<th align="left">Command Line Options Format</th>
<th align="left">Reference</th>
</tr>

<tr>
<td> {{site.data.keyword.IBM_notm}}JRE</td>
<td>includes runtime options (prefixed by -X), any Java system properties (prefixed with -D), and does not recommend -XX for the casual usage (these options are subject to change)
</td>
<td>[Version 8 command-line options](http://www-01.ibm.com/support/knowledgecenter/SSYKE2_8.0.0/com.ibm.java.lnx.80.doc/diag/appendixes/cmdline/cmdline.html), [Version 7 command-line options](http://www-01.ibm.com/support/knowledgecenter/SSYKE2_7.0.0/com.ibm.java.lnx.70.doc/diag/appendixes/cmdline/cmdline.html)
</td>
</tr>

<tr>
<td> OpenJDK </td>
<td>is based on the HotSpot runtime that has the notation of -X for non-standard, -XX for developer options, and Boolean flags to enable or disable the option </td>
<td>[HotSpot Runtime Overview  ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://openjdk.java.net/groups/hotspot//docs/RuntimeOverview.html) </td>
</tr>
</table>

An application that requires customized JVM options can set the option as a value for one of the environment variables IBM_JAVA_OPTIONS, JAVA_OPTS, or JVM_ARGS in {{site.data.keyword.Bluemix_notm}}. Refer to the Environment Variables section on how to set an application's environment variable. A packaged server or a server directory can also include a jvm.options file that contains the command line options instead of setting an environment variable.

When the JVM options are applied to the JRE, the Liberty buildpack's default options are applied first, followed by the customized options. The customized options are appended in a specific order, which is listed in the table. The sequence of the applied Java options defines which options take precedence. Options that are applied last have precedence over options that were previously applied.

Note: Some options might not go into effect unless the option is triggered by an agent.

<table>
<tr>
<th align="left">Applied order</th>
<th align="left">Application JVM options setting</th>
<th align="left">Description</th>
<th align="left">Supported application type</th>
<th align="left">To update the JVM option of a deployed application</th>
<th align="left">Applicable to OpenJDK JRE</th>
</tr>

<tr>
<td>1</td>
<td>IBM_JAVA_OPTIONS</td>
<td>an environment variable that is supported by the {{site.data.keyword.IBM_notm}} JRE</td>
<td>All</td>
<td>Restart or restage the application</td>
<td>No</td>
</tr>

<tr>
<td>2</td>
<td>JAVA_OPTS</td>
<td>an environment variable through the Liberty buildpack Java Options framework</td>
<td>All</td>
<td>Restage the app</td>
<td>Yes</td>
</tr>

<tr>
<td>3</td>
<td>jvm.options</td>
<td>a JVM configuration file that is supported by the Liberty runtime packaged server or server directory</td>
<td>Server package</td>
<td>Restage the app</td>
<td>Yes</td>
</tr>

<tr>
<td>4</td>
<td>JVM_ARGS</td>
<td>an environment variable that is supported by the Liberty runtime</td>
<td>All</td>
<td>Restart or restage the app</td>
<td>Yes</td>
</tr>
</table>

### Determining the applied JVM options of a running application
{: #determining_applied_jvm_options}

Except for application-defined options that are specified with the JVM_ARGS environment variable, the resulting options are persisted in the runtime environment either as command line options (stand-alone Java applications) or in a `jvm.options` file (non-standalone Java applications). The applied JVM options for the application can be viewed either from the {{site.data.keyword.Bluemix_notm}} console or the {{site.data.keyword.Bluemix_notm}} CLI.

The JVM options for stand-alone Java application are persisted as command line options. They can be viewed from the `staging_info.yml` file.

To view the `staging_info.yml` file on an application running in a DEA node, run:

```
    ibmcloud cf files myapp staging_info.yml
```
{: codeblock}

To view the `staging_info.yml` file on an application running in a Diego cell, run:

```
    ibmcloud cf ssh myapp -c "cat staging_info.yml"
```
{: codeblock}

The JVM options for WAR, EAR, server directory and packaged server deployment are persisted in a `jvm.options` file. The `jvm.options` file can be found in the `app/wlp/usr/servers/<serverName>/` directory. In the most cases the `<serverName>` is set to `defaultServer` unless a packaged server was deployed with a different server name. For example:

To view the `jvm.options` file on an application running in a DEA node, run:

```
    ibmcloud cf files myapp app/wlp/usr/servers/defaultServer/jvm.options
```
{: codeblock}

To view the `jvm.options` file on an application running in a Diego cell, run:

```
    ibmcloud cf ssh myapp -c "cat app/wlp/usr/servers/defaultServer/jvm.options"
```
{: codeblock}


#### Example usage
{: #example_usage}

Deploying an application with customized JVM options to enable {{site.data.keyword.IBM_notm}} JRE verbose garbage collection logging:
* The JVM options included in an application's `manifest.yml` file:

```
    env:
      JAVA_OPTS: "-verbose:gc -Xverbosegclog:./verbosegc.log,10,1000"
```
{: codeblock}

* To view the JVM generated verbose garbage collection log file on an application running in a DEA node, run:

```
    ibmcloud cf files myapp app/wlp/usr/servers/defaultServer/verbosegc.log.001
```
{: codeblock}

* To view the JVM generated verbose garbage collection log file on an application running in a Diego cell, run:

```
    ibmcloud cf ssh myapp -c "cat app/wlp/usr/servers/defaultServer/verbosegc.log.001"
```
{: codeblock}

* To update a deployed application's {{site.data.keyword.IBM_notm}} JRE option to trigger a heap, snap, and javacore on an OutOfMemory condition, set the application's environment variable with the JVM option and restart the application:

```
    ibmcloud cf set-env myapp JVM_ARGS '-Xdump:heap+java+snap:events=systhrow,filter=java/lang/OutOfMemoryError'
    ibmcloud cf restart myapp
```
{: codeblock}

 See the [Logging and tracing](/docs/cloud-foundry?topic=cloud-foundry-logging_tracing#download_dumps) documentation for details on viewing and downloading the generated dump files.

### Overlaying the JRE
{: #overlaying_jre}

There are some cases where files need to be bundled with the JRE to expose their functions. The application developer can supply JRE files for customization.

The files to be overlaid can be packaged with the application WAR, EAR, or JAR in a resources folder at the root of the archive. For a server (compressed file or server directory), the files can be packaged in a resources folder in the server directory, with the server.xml file.

* WAR file
  * WEB-INF
  * resources
    * other files
    * .java-overlay


* EAR file
  * META-INF
  * resources
    * other files
    * .java-overlay


* JAR file
  * META-INF
  * resources
    * other files
    * .java-overlay


* server_name DIR
  * apps
  * dropins
  * server.xml
  * resources
    * other files
    * .java-overlay

The .java-overlay directory contains specific files in the same file hierarchy as the Java JRE being overlaid starting with .java/jre.

For example, if you want to use AES 256-bit encryption, you need to overlay these Java policy files:

```
    .java\jre\lib\security\US_export_policy.jar
    .java\jre\lib\security\local_policy.jar
```
{: codeblock}

Download the appropriate unrestricted policy files and add them to your application as:

```
    resources\.java-overlay\.java\jre\lib\security\US_export_policy.jar
    resources\.java-overlay\.java\jre\lib\security\local_policy.jar
```
{: codeblock}

When you push your application, these jars overlay the default policy jars in the Java runtime. This process enables AES 256-bit encryption.
