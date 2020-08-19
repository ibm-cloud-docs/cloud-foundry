---

copyright:
  years: 2016, 2018
lastupdated: "2018-06-27"
subcollection: cloud-foundry

---

{:external: target="_blank" .external}
{:codeblock: .codeblock}

# Use Dynatrace to monitor Liberty in {{site.data.keyword.cloud_notm}}
{: #using_dynatrace}

Dynatrace is a third-party service that provides monitoring for your app. You can integrate Dynatrace with your Liberty application, but IBM does not provide support for third-party services. See [Third-party services](/docs/cloud-foundry?topic=cloud-foundry-buildpack_support_statement#third-party) for more information.

For more information about Dynatrace and its licensing, see [Dynatrace Application Monitoring](http://www.dynatrace.com/en/products/application-monitoring.html){: external}.

When your Liberty application is configured to use Dynatrace, the default behavior is that the
Liberty runtime will acquire a Dynatrace agent `.jar` file from a Dynatrace site and run
that Dynatrace agent with your app.  With that default behavior the minimal necessary
configuration to use Dynatrace is to create a user-provided service that points to
your Dynatrace collector.

## Creating a user-provided service that points to your Dynatrace collector

First, you'll need to set up a Dynatrace collector.  Then you must create a user-provided
service to pass information for the Dynatrace agent to connect with the Dynatrace collector. See [Dynatrace Architecture](https://community.dynatrace.com/community/display/DOCDT65/Architecture){: external} to better understand the relationship between Dynatrace components.

1. Set up a Dynatrace collector.
  * See the [Dynatrace community website ![External link icon](../../../icons/launch-glyph.svg "External link icon")](https://community.dynatrace.com/community/display/EVAL/Step+3+-+Connect+Agent+to+Dynatrace) for instructions on downloading and setting up the Dynatrace collector.
  * Ensure that the collector is set up in a location that is accessible to the Dynatrace agent running with your app in {{site.data.keyword.Bluemix_notm}}.
2. Create a user-provided service that points to the running Dynatrace collector.

  **Note:** The name of the user-provided service must contain the string **dynatrace**. Case is ignored. For example, use the command that follows, where **my-dynatrace-collector** contains **dynatrace**:
  ```
  ibmcloud cf cups my-dynatrace-collector -p '{"server":"DynatraceCollectorIPaddress","profile":"Monitoring"}'
  ```
  {: codeblock}

    In this example, my-dynatrace-collector is the name given to the service, DynatraceCollectorIPaddress is the IP address of the Dynatrace collector you     have configured, and profile is the optional Dynatrace profile name associated with this monitored app. The default profile value is Monitoring. You can specify optional parameters as in the example that follows.

    ```
    ibmcloud cf cups my-dynatrace-collector -p '{"server":"DynatraceCollectorIPaddress","profile":"Monitoring",
                      "options" : {"dynatrace-parameter-1": "value",
                                   "dynatrace-parameter-2": "value"}}'
    ```
    {: codeblock}

    See the [_Agent Settings_ section of Agent Configuration ![External link icon](../../../icons/launch-glyph.svg "External link icon")](https://community.dynatrace.com/community/display/DOCDT65/Set+up+Agents) at the Dynatrace community website for more information about available options. For example, using the exclude option, you can exclude classes from being monitored by Dynatrace. See [Dynatrace Agent Framework ![External link icon](../../../icons/launch-glyph.svg "External link icon")](https://github.com/cloudfoundry/ibm-websphere-liberty-buildpack/blob/master/docs/framework-dynatrace-agent.md) for more details about configuring the user-provided service.

3. After you push your app to {{site.data.keyword.Bluemix_notm}}, bind the user-provided service that you created to the app. For example, use the following command:
  ```
  ibmcloud cf bs myApp my-dynatrace-collector
  ```
  {: codeblock}

    **Note:** You must restage your application after binding the service.

## Optional configuration
{: #optional_configuration}

You may choose to acquire and host the Dynatrace agent `.jar` file yourself.  In that case the following
additional configuration steps are needed.
1. Acquire and host the Dynatrace agent `.jar` file so that the Liberty buildpack can download it.
2. Configure your Liberty app so that it can download the Dynatrace agent.

### Hosting the Dynatrace agent
{: #hosting_dynatrace_agent}
The Dynatrace agent must be hosted on a web server, and the Liberty buildpack must be able to download the agent `.jar` file from that server. The server must be configured with an `index.yml` file that specifies details about the agent `.jar` file. Complete the steps that follow to set up the Dynatrace agent:
  1. Download the Dynatrace agent `.jar` file. See [Dynatrace Server Platform Installers ![External link icon](../../../icons/launch-glyph.svg "External link icon")](https://community.dynatrace.com/community/display/EVAL/Step+1+-+Download+and+install+Dynatrace) at the Dynatrace community website for instructions on downloading the Dynatrace agent `.jar` file. The appropriate agent `.jar` file for running on {{site.data.keyword.Bluemix_notm}} is the **dynatrace-agent-unix.jar** version **6.+**.
  2. Host the agent `.jar` file in a location from which the Liberty buildpack can download it. You can host it on {{site.data.keyword.Bluemix_notm}} itself using any of the available server facilities, or you can host it on some publicly available location.
     * Ensure that you provide a `index.yml` file at the hosting location. The `index.yml` file must contain an entry consisting of the version ID of the agent `.jar` file follow by a colon and the complete URL of the location of that agent `.jar` file. For example:

            ---
               6.3.0: https://my-dynatrace-agent.mybluemix.net/dynatrace-agent-6.3.0-unix.jar
            {: codeblock}

     * The **dynatrace-agent-6.3.0-unix.jar** file must be available at the location specified in the `index.yml` file. The location for both the `.jar` file and the `index.yml` can be the same directory.

### Configuring the Liberty app
{: #configuring_liberty_app}

The Liberty app you want to monitor must be configured to locate the server hosting the agent `.jar` file you previously set up. You can configure the app with the **JBP_CONFIG_DYNATRACEAPPMONAGENT** environment variable. The **JBP_CONFIG_DYNATRACEAPPMONAGENT** environment variable tells the buildpack where to download the Dynatrace agent from. To set the environment variable, complete these steps:

1. Set the variable **JBP_CONFIG_DYNATRACEAPPMONAGENT** so it has the value *"repository_root: URL_of_server_hosting_index.yml"*. For example, after pushing your application issue the following command:

        ibmcloud cf se myApp JBP_CONFIG_DYNATRACEAPPMONAGENT 'repository_root: https://my-dynatrace-agent-host.mybluemix.net'
        {: codeblock}

    In this example, *my-dynatrace-agent-host.mybluemix.net* is the URL of the `index.yml` file hosted by the server that you previously configured.

2. After you set the environment variable, restage your app. Check the staging log for a message indicating successful download of the Dynatrace agent from your agent hosting server. For example:
```
    Downloading dynatrace-agent-6.3.0-unix.jar 6.3.0 from https://my-dynatrace-agent-host.mybluemix.net/dynatrace-agent-6.3.0-unix.jar (17.8s)
```
{: codeblock}
