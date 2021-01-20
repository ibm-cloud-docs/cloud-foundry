---

copyright:
  years: 2018, 2021
lastupdated: "2021-01-21"

keywords: getting started tutorial, IBM Cloud, Cloud Foundry Enterprise Environment

subcollection: cloud-foundry

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}

{{site.data.keyword.cfee_full}} is deprecated. The most recent documentation updates for {{site.data.keyword.ibmcf_notm}} can be found in the [{{site.data.keyword.ibmcf_notm}} version of this information](/docs/cloud-foundry-public?topic=cloud-foundry-public-getting-started).
{: important}

# Getting started with {{site.data.keyword.cfee_full_notm}}
{: #getting-started}

<!-- Revamp the getting started to guide the user from the CF overview page in the console, starting with selecting Enterprise Environment. One of the prereqs should be setting up the IBM Cloud environment and point to the Determining your organization architecture topic. Also, CFEE is not an approved acronym. Replace all instances with the Enterprise Environment short name conref. -->

In this {{site.data.keyword.cfee_full}} getting started tutorial, we add users to an instance, create an organization and spaces, deploy apps, and bind those apps to services.
{: shortdesc}

## Before you begin
{: #prereqs}

* Ensure that you're in the {{site.data.keyword.Bluemix_notm}} account where you want to create the instance.
* Ensure that you have the correct [permissions](/docs/cloud-foundry?topic=cloud-foundry-permissions).
* [Prepare your IBM Cloud account](/docs/cloud-foundry?topic=cloud-foundry-prepare) to ensure that it can create the infrastructure resources required for an instance.
* Create a CFEE instance from the [CFEE page in the {{site.data.keyword.Bluemix_notm}} catalog](https://cloud.ibm.com/cfadmin/create). For more information, see [Creating a CFEE instance](/docs/cloud-foundry?topic=cloud-foundry-create-environment).


## Step 1. Create organizations and spaces
{: #create-orgsandspaces}

After your instance is created, structure the environment by creating organizations and spaces. Apps in an {{site.data.keyword.cfee_full_notm}} instance are scoped within specific spaces. In turn, a space exists within a specific organization. Members of an organization share a quota plan, apps, services instances, and custom domains. For more information, see [Determining your organization architecture](/docs/cloud-foundry?topic=cloud-foundry-orgstructure).

1. In the CFEE user interface, click **Organizations** in the navigation pane.

    To get to the CFEE user interface, go to the [{{site.data.keyword.cfee_full_notm}}s dashboard](https://cloud.ibm.com/cloudfoundry/environments){: new_window} and open the {{site.data.keyword.cfee_full_notm}} instance where you want to create organizations.
    {: tip}

3. Click **Create Organization**.
4. Enter a **Name** for the new organization.
5. Under **Managers**, identify at least one user. Users with a Manager role can add members to that organization.
6. Under **Quota plan**, select an available plan. A quota plan limits the memory available for apps in the organization, the maximum number of apps instances hosted, and the maximum number of routes.

    You can select a different quota at a later time. You can also create your own custom quotas in the **Quotas** page of the CFEE user interface. You can make a custom quota the _Default_ quota by clicking the _Copy to default_ action from the quota's overflow menu, which copies the values of the custom quota into the default quota.
    {: tip}

1. Click **Add** to create the organization.
1. On the Organizations page, click the name of the organization you created.
1. Click the **Spaces** tab and click **Create Space**.
1. Enter a name for the space, select at least one manager, and click **Add**.

## Step 2. Add users to organizations and spaces
{: #add-users}

[Add users](/docs/cloud-foundry?topic=cloud-foundry-adding_users) to those organizations and spaces under specific role assignments controlling their level of access.  Before users can be added as members of organizations and spaces in a CFEE, those users must have access to the CFEE instance. See [Permissions](/docs/cloud-foundry?topic=cloud-foundry-permissions).

1. On the Spaces tab, click the name of the space you created.
1. On the Members tab, click **Add members**.

## Step 3. Deploy and view applications
{: #deploy-apps}

You can [deploy apps](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps) to your CFEE instance with the {{site.data.keyword.Bluemix_notm}} command line interface.  View the list of deployed applications in the user interface, either in the context of a specific CFEE space, or globally across all CFEE instances.  You can also start, stop, or delete applications from those views.

1. [Download and install the Cloud Foundry CLI](https://docs.cloudfoundry.org/cf-cli/install-go-cli.html){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").
1. Change to the directory where your code is located. `cd <your_directory>`
2. In the CFEE user interface, go to the Overview page and copy the environment's API endpoint.
3. In the command line interface, set the API endpoint for your environment:

  ```
  cf api <api_endpoint>
  ```
  {: pre}

4. Log in to the environment.

  ```
  cf login -u <username> -o <org_name> -s <space_name>
  ```
  {: pre}

  If you're using a federated ID, use the `-sso` option.

  ```
  cf login -o <org_name> -s <space_name> -sso
  ```
  {: pre}

  **Note**: You must add single or double quotation marks around `username`, `org_name`, and  `space_name` if the value includes a space, for example, `-o "my org"`.

5.  Deploy your app to {{site.data.keyword.Bluemix_notm}} by using the `ibmcloud cf push` command. For more information about the `cf app push` command, see [Deploying apps](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps).

  ```
  ibmcloud cf push <app_name>
  ```
  {: pre}

6.  Access your app by browsing to `https://<app_url>.<AppDomainName>`.


## Step 4. Bind applications to service instances
{: #bind-apps}

[Create services](/docs/cloud-foundry?topic=cloud-foundry-workingwith-services#creating-services-inspace) or [Add existing services](/docs/cloud-foundry?topic=cloud-foundry-workingwith-services#adding-services-inspace) from your IBM Cloud account to the CFEE space so you can bind the services to the applications you deployed.

1. In the CFEE user interface, navigate to the **Organizations > *your-org* > Spaces > *your-space*** page and go to the Services tab.
1. Click **Create service** to provision a new service or click **Add service** to add an existing service from your IBM Cloud account.
1. On the Services tab, locate the service instance you want to bind and select **Bind to application** from the service's overflow menu.
6. Select the application that you want to bind to the service instance.

In the [Cloud Foundry dashboard](https://cloud.ibm.com/dashboard/cloudfoundry/overview){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon") you can see a consolidated view of all applications and services, both *public* and *enterprise*. Click *Public* in the left navigation pane to see the public applications and services available in your IBM Cloud account.  Click on *Enterprise* to see all the CFEE environments, applications deployed into CFEE spaces, and services available to CFEE spaces.
{: tip}

## Next steps
{: #next-steps}

You can do the following tasks to manage your environment if it was created from the **Standard** plan:

 * Enable the environment for [auditing events](/docs/cloud-foundry?topic=cloud-foundry-auditing-logging#auditing) and [logging persistence](/docs/cloud-foundry?topic=cloud-foundry-auditing-logging#logging).

 * [Enable monitoring tools](/docs/cloud-foundry?topic=cloud-foundry-monitoring) after the CFEE instance is created. The monitoring toolset includes Prometheus, Grafana, and Alertmanager. Monitoring tools are not automatically provisioned on CFEE instances v2.2.0 or later.

 * [Create  Cloud Foundry domains](/docs/cloud-foundry?topic=cloud-foundry-domains) for all applications in an environment  (shared domains) or for a specific organization (private domains), and secure them with SSL certificates.

 * Configure the prioritization order of the Cloud Foundry buildbacks. [Buildpacks](https://docs.cloudfoundry.org/buildpacks/) provide the runtime support for applications deployed in a Cloud Foundry environment, automatically configuring the runtime for an application and handling its dependencies. Cloud Foundry includes a set of buildpacks for common languages and frameworks. You can create and upload custom buildpacks in the **Buildpacks** page of the CFEE user interface.

   Buildpacks have an ordinal position in the priority list.  During the staging of an application, Cloud Foundry checks the compatibility of the application against the set of buildpacks starting with position 1. The compatibility checks proceeds down the priority list until it finds a compatible buildpack. Ensure that the priority sequence of the buildpack set meets the needs of your development teams.  You can change the position of a buildpack in the priority sequence by dragging and dropping the buildpack name into a different position.  You can also manage buildpacks through the [Cloud Foundry CLI](https://docs.cloudfoundry.org/adminguide/buildpacks.html).

Regardlesss of whether your CFEE instance was created from the **Standard** plan or the **Eirini Technical Preview** plan,  you can [install the Stratos Console](/docs/cloud-foundry?topic=cloud-foundry-stratos) to manage your environment's organizations, spaces, and applications.

You can perform some administrations tasks in a CFEE usig `ibmcloud CFEE` CLI commands. The commands allow you to get information about a CFEE instance, as well as to manage its organizations and spaces. See [IBM Cloud CLI CFEE command reference](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_commands_cfee){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").

You can find videos with in-depth discussions and demonstrations on various CFEE topics in the [CFEE video playlist](https://ibm.biz/CFEE-Playlist){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").

For information about the CFEE APIs, see the [CF Admin API documentation](https://cloud.ibm.com/apidocs/cfaas){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").
