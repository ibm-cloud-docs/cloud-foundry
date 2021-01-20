---

copyright:
  years: 2015, 2021
lastupdated: "2021-01-20"
subcollection: cloud-foundry

---

{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:important: .important}
{:note: .note}

{{site.data.keyword.cfee_full}} is deprecated. The most recent documentation updates for {{site.data.keyword.ibmcf_notm}} can be found in the [{{site.data.keyword.ibmcf_notm}} version of this information](/docs/cloud-foundry-public?topic=cloud-foundry-public-nodejs-latest_updates).
{: important}

# Latest updates to the SDK for Node.js buildpack
{: #nodejs-latest_updates}

A list of the latest updates in the sdk-for-nodejs buildpack.

## September 8, 2020: Updated Node.js buildpack v4.4-20200828-1028

The SDK for Node.js buildpack v4.3 provides Node.js community runtime versions v10.21.0, v.10.22.0, v12.18.2, v12.18.3. The default is latest 10.x, so it is currently 10.21.0.  This buildpack is based on the community node.js buildpack [v1.7.26](https://github.com/cloudfoundry/nodejs-buildpack/tree/v1.7.26).


## June 8, 2020: Updated Node.js buildpack v4.3-20200606-1928

The SDK for Node.js buildpack v4.3 provides Node.js community runtime versions v10.20.1, v10.21.0, v12.17.0, v12.18.0. The default is latest 10.x, so it is currently 10.21.0.  This buildpack is based on the community node.js buildpack [v1.7.20](https://github.com/cloudfoundry/nodejs-buildpack/tree/v1.7.20).  

This release also includes CVE-2020-8172, CVE-2020-11080, CVE-2020-8174 and CVE-2020-10531:
* [June 2020 Security Releases](https://nodejs.org/en/blog/vulnerability/june-2020-security-releases/)


## April 21, 2020: Updated Node.js buildpack v4.2.1-20200420-1206

The SDK for Node.js buildpack v4.2.1 provides Node.js community versions v10.19.0, v10.20.1, v12.16.1, v12.16.2. The default is latest 10.x, so it is currently 10.20.1.  This buildpack is based on the community node.js buildpack [v1.7.17](https://github.com/cloudfoundry/nodejs-buildpack/tree/v1.7.17).  

This release also includes CVE-2019-1551.

## March 2, 2020: Updated Node.js buildpack v4.2

The SDK for Node.js buildpack v4.2 provides Node.js community versions v10.18.1, v10.19.0, v12.16.0, v12.16.1. The default is latest 10.x, so it is currently 10.19.0.  This buildpack is based on the community node.js buildpack [v1.7.13](https://github.com/cloudfoundry/nodejs-buildpack/tree/v1.7.13).  

Beginning with this buildpack, the Node.js v8.x runtimes are no longer included.   
{: important}

This release also includes CVE-2019-15605, CVE-2019-15606, CVE-2019-15604:
* [February 2020 Security Releases](https://nodejs.org/en/blog/vulnerability/february-2020-security-releases/)

## December 11, 2019: Updated Node.js buildpack v4.1

The SDK for Node.js buildpack v4.1 provides Node.js community versions v8.16.1, v8.16.2, v10.16.3, v10.17.0, v12.11.1, v12.13.0. The default is latest 10.x, so it is currently 10.17.0.  This buildpack is based on the community node.js buildpack [v1.7.3](https://github.com/cloudfoundry/nodejs-buildpack/releases/tag/v1.7.3).  

## September 24, 2019: Updated Node.js buildpack v4.0

The SDK for Node.js buildpack v4.0 provides Node.js community versions v8.16.0, v8.16.1, v10.16.0, v10.16.3, v12.7.0, v12.8.1. The default is latest 10.x, so it is currently 10.16.0.  

The sdk-for-nodejs buildpack was rebased on the community node.js buildpack v1.6.53 and contains some [important changes](https://www.ibm.com/cloud/blog/upcoming-important-changes-to-the-sdk-for-nodejs-buildpack).
{: important}

In addition, this buildpack contains fixes for the following security vulnerabilities:  CVE-2019-9516 CVE-2019-9515 CVE-2019-9518 CVE-2019-9517 CVE-2019-9512 CVE-2019-9511 CVE-2019-9514 CVE-2019-9513.

## July 16, 2019: Updated Node.js buildpack v3.28

The SDK for Node.js buildpack v3.28 provides IBM SDK for Node.js versions 4.8.5, 4.8.7 and Node.js community versions 8.15.1, 8.16.1, 10.15.0, 10.16.0 and 12.5.0. The default is latest 10.x, so it is currently 10.16.0.  

## May 31, 2019: Updated Node.js buildpack v3.27

The SDK for Node.js buildpack v3.27 provides IBM SDK for Node.js versions 4.8.5, 4.8.7 and Node.js community versions 6.17.0, 6.17.1, 8.15.1, 8.16.1, 10.15.0 and 10.16.0. The default is latest 6.x, so it is currently 6.17.1.  This is the last SDK for Node.js buildpack that includes v6.x runtimes.  

## March 18, 2019: Updated Node.js buildpack v3.26

The SDK for Node.js buildpack v3.26 provides IBM SDK for Node.js versions 4.8.5, 4.8.7 and Node.js community versions 6.16.0, 6.17.0, 8.15.0, 8.15.1, 10.15.0 and 10.15.3. The default is latest 6.x, so it is currently 6.17.0.

## January 23, 2019: Updated Node.js buildpack v3.25.1

The SDK for Node.js buildpack v3.25.1 provides IBM SDK for Node.js versions 4.8.5, 4.8.7 and Node.js community versions 6.14.4, 6.16.0, 8.11.4, 8.15.0, 10.10.0 and 10.15.0. The default is latest 6.x, so it is currently 6.16.0. The versions 6.15.0, 8.14.0 and 10.14.0 that were included in the last buildpack had a regression. The regressions has been fixed in 6.16.0, 8.15.0 and 10.15.0 which are now included instead.

## January 7, 2019: Updated Node.js buildpack v3.25

The SDK for Node.js buildpack v3.25 provides IBM SDK for Node.js versions 4.8.5, 4.8.7 and Node.js community versions 6.14.4, 6.15.0, 8.11.4, 8.14.0, 10.10.0 and 10.14.0. The default is latest 6.x, so it is currently 6.15.0. The buildpack also fixes a minor bug in the Dynatrace hook.

## December 5, 2018: Updated Node.js buildpack v3.24

The SDK for Node.js buildpack v3.24 provides IBM SDK for Node.js versions 4.8.5, 4.8.7 and Node.js community versions 6.14.3, 6.14.4, 8.11.3, 8.11.4, 10.9.0 and 10.10.0. The default is latest 6.x, so it is currently 6.14.4. The buildpack also fixes a minor bug in the Dynatrace hook.

## September 7, 2018: Updated Node.js buildpack v3.22
{:#fips-deprecation}

Beginning with this buildpack, the SDK for Node.js buildpack includes the Node.js community release runtimes for version 6.x and 8.x. With this change, the Node.js OpenSSL FIPS module is no longer included in these versions of the buildpack. Only version 4.x continues to include the OpenSSL FIPS module.  
{: important}

The SDK for Node.js buildpack v3.22 provides IBM SDK for Node.js versions 4.8.5, 4.8.7 and Node.js community versions 6.14.3, 6.14.4, 8.11.3 and 8.11.4. The default is latest 6.x, so it is currently 6.14.4.

This release also includes fixes for the following security vulnerability:
* [CVE-2018-0732](https://www-01.ibm.com/support/docview.wss?uid=swg22012749)

## July 24, 2018: Updated Node.js buildpack v3.21

Beginning with the latest Node.js 6.x and 8.x versions in this release, the SDK for Node.js buildpack is based on the Node.js community release. With this change, the Node.js OpenSSL FIPS module in the buildpack will no longer be updated. The current OpenSSL FIPS module and IBM SDK for Node.js builds are eligible for removal as of 24 August 2018. For more information, see the [Aligning the Node.js Buildpack to Community Runtimes ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud/blog/announcements/aligning-the-node-js-buildpack-to-community-runtimes) blog post.
{: important}

The SDK for Node.js buildpack v3.21 provides IBM SDK for Node.js versions 4.8.5, 4.8.7, 6.13.0 and 8.9.4 and Node.js community versions 6.14.3 and 8.11.3. The default is latest 6.x, so it is currently 6.14.3.

This release also includes fixes for the following security vulnerability:
* [CVE-2018-0739](http://www.ibm.com/support/docview.wss?uid=swg22016251)

## June 1, 2018: Updated Node.js buildpack v3.20.2
The SDK for Node.js buildpack v3.20.2 adds Dynatrace Managed PaaS integration for the current Node.js runtimes.

## May 17, 2018: Updated Node.js buildpack v3.20.1
The SDK for Node.js buildpack v3.20.1 fixes Dynatrace PaaS integration for the current Node.js runtimes.

## April 9, 2018: Updated Node.js buildpack v3.20
The SDK for Node.js buildpack v3.20 adds Dynatrace PaaS integration for the current Node.js runtimes.

## March 16, 2018: Updated Node.js buildpack v3.19
The SDK for Node.js buildpack v3.19 provides IBM SDK for Node.js versions 4.8.5, 4.8.7, 6.12.3, 6.13.0, 8.9.3 and 8.9.4. The default is latest 6.x, so it is currently 6.13.0.

## February 6, 2018: Updated Node.js buildpack v3.18
The SDK for Node.js buildpack v3.18 provides IBM SDK for Node.js versions 4.8.5, 4.8.7, 6.12.2, 6.12.3, 8.9.3 and 8.9.4. The default is latest 6.x, so it is currently 6.12.3.

## January 8, 2018: Updated Node.js buildpack v3.17
The SDK for Node.js buildpack v3.17 provides IBM SDK for Node.js versions 4.8.5, 4.8.7, 6.12.0, 6.12.2, 8.9.0 and 8.9.3. The default is latest 6.x, so it is currently 6.12.2.

## December 11, 2017: Updated Node.js buildpack v3.16.1
The SDK for Node.js buildpack v3.16.1 provides IBM SDK for Node.js versions v4.8.4, v4.8.5, v6.11.4, v6.12.0, v8.6.0, v8.9.0. The default is latest 6.x, so it is currently 6.12.0.
Please note that it fixes PSIRTs: Advisory ID: 10237 Product Record ID: 104487 Title: Node.js zlib DOS security vulnerability, October 2017 (CVE-2017-14919). It is recommended to upgrade to v3.16.1 to get fixes for security vulnerabilities affecting 8.6.0.0 and earlier, 6.10.2.0 to 6.11.4.0 and 4.8.2.0 to 4.8.4.0.

## November 1, 2017: Updated Node.js buildpack v3.15
The SDK for Node.js buildpack v3.15 provides IBM SDK for Node.js versions 4.8.3, 4.8.4, 6.11.3, 6.11.4, 8.3.0 and 8.6.0. The default is latest 6.x, so it is currently 6.11.4.

## September 20, 2017: Updated Node.js buildpack v3.14
The SDK for Node.js buildpack v3.14 provides IBM SDK for Node.js versions 4.8.3, 4.8.4, 6.11.2, 6.11.3, 8.1.4 and 8.3.0. The default is latest 6.x, so it is currently 6.11.3. A buildpack bug that prevented Node.js apps from [shutting down gracefully](https://docs.cloudfoundry.org/devguide/deploy-apps/app-lifecycle.html#shutdown) was fixed in this release.

## July 26, 2017: Updated Node.js buildpack v3.13
The SDK for Node.js buildpack v3.13 provides IBM SDK for Node.js versions 4.8.3, 4.8.4, 6.11.0, 6.11.1, 8.1.2 and 8.1.4. The default is latest 6.x, so it is currently 6.11.1. Please note that version 8 is available for testing but is not yet recommended for production.  

This buildpack contains updated Node.js versions which address recent security vulnerabilities found in Node.js. Users should update their applications to use the latest versions available and then restage the applications in {{site.data.keyword.Bluemix_notm}}.  See <a href="http://www-01.ibm.com/support/docview.wss?uid=swg22006722">this security bulletin</a> for details on the CVE-2017-1000381 and CVE-2017-11499 fixes for Node.js security vulnerabilities.

## May 5, 2017: Updated Node.js buildpack v3.12
The SDK for Node.js buildpack v3.12 provides IBM SDK for Node.js versions 0.12.17, 0.12.18, 4.8.0, 4.8.2, 6.10.0 and 6.10.2. The default is now changed from the latest 4.x to latest 6.x, so it is currently 6.10.2. Being a major version change, this could affect apps that are relying on the default. See [Node.js version long-term support and the SDK for Node.js buildpack](https://www.ibm.com/blogs/bluemix/2016/11/node-version-support-and-sdk-buildpack/) for more information about how to avoid any problems.

In addition to the new runtimes, this release contains a buildpack bug fix an issue with the App Management Health Center handler and Node.js versions 6.9.5 and 6.10.0.

## March 10, 2017: Updated Node.js buildpack v3.11
This release of the buildpack supports IBM SDK for Node.js runtime versions: 0.10.47, 0.10.48, 0.12.17, 0.12.18, 4.7.3, 4.8.0, 6.9.5, and 6.10.0. The default version now is 4.8.0.

In addition to the new runtimes, this release contains a fix for a bug encountered when enabling the shell app management handler using the devconsole UI. This buildpack also changes the way auto-configuration works for the Monitoring and Analytics service. Applications using the Free plan will no longer have the log capability added to their applications, it is being replaced by logmet.

## January 20, 2017: Updated Node.js buildpack v3.10
This release of the buildpack supports IBM SDK for Node.js runtime versions: 0.10.47, 0.10.48, 0.12.17, 0.12.18, 4.7.0, 4.7.2, 6.9.2, and 6.9.4. The default is now 4.7.2.  It is also synchronized with the [Cloud Foundry Node.js buildpack v1.5.24](https://github.com/cloudfoundry/nodejs-buildpack/tree/v1.5.24).
It contains a fix for a bug where "npm start" was not always called to start applications.

## November 17, 2016: Updated Node.js buildpack v3.9
This release of the buildpack supports IBM SDK for Node.js runtime versions: 0.10.47, 0.10.48, 0.12.16, 0.12.17, 4.6.1, 4.6.2, 6.7.0, and 6.9.1. The default is now 4.6.2.

Note that Node.js v6 was promoted to LTS status on October 18, 2016 and will soon become the buildpack's default runtime. Node.js v0.10 reached end of life on October 31, 2016 and will soon no longer be included in the buildpack. See [Node.js version long-term support and the SDK for Node.js buildpack](https://www.ibm.com/blogs/bluemix/2016/11/node-version-support-and-sdk-buildpack/) for more details.

Bugs affecting the trace and inspector App Management handlers, when used in conjunction with Node.js v6, have been addressed in this release. See [Managing Liberty and Node.js apps](../common/app_mng.html#inspector) for more information about how the inspector handler is changing now that Node.js v6 has integrated the inspector capability.

## October 7, 2016: Updated Node.js buildpack v3.8-20161006-1211
This release of the buildpack supports IBM SDK for Node.js runtime versions: 0.10.46, 0.10.47, 0.12.15, 0.12.16, 4.5.0, 4.6.0, 6.6.0, and 6.7.0. The default is now 4.6.0.

In addition to the new runtimes, this release contains buildpack bug fixes. A fix for the known issue when using Node.js 6.x and Development Mode that was mentioned in the v3.7-20160826-1101 release updates is one of them. It is also synchronized with the [Cloud Foundry Node.js buildpack v1.5.20](https://github.com/cloudfoundry/nodejs-buildpack/tree/v1.5.20).

## August 26, 2016: Updated Node.js buildpack v3.7-20160826-1101
This release of the buildpack supports IBM SDK for Node.js runtime versions: 0.10.45, 0.10.46, 0.12.14, 0.12.15, 4.4.7, 4.5.0, 6.2.2, and 6.4.0. The default is now 4.5.0.

This release includes bug fixes, including those from the [Cloud Foundry’s Node.js buildpack 1.5.18](https://github.com/cloudfoundry/nodejs-buildpack/tree/v1.5.18).

The release removes support for the strongpm App Management handler as announced in [{{site.data.keyword.Bluemix_notm}} Node.js Buildpack v3.3 – FIPS mode and more](https://developer.ibm.com/bluemix/2016/05/05/node-buildpack-update-fips-mode/).

Note that there is a known issue when using Node.js 6.x and [Development Mode](../common/app_mng.html#devmode). As a work around you will need to restage your application after enabling Development Mode before you can begin using it.

## July 22, 2016: Updated Node.js buildpack v3.6-20160715-0749
This release of the buildpack supports IBM SDK for Node.js runtime versions: 0.10.45, 0.10.46, 0.12.14, 0.12.15, 4.4.6, 4.4.7, 6.2.1, and 6.2.2. The default is now 4.4.7.

This release includes an updated App Management proxy that supports federated logins.

Included are fixes for the following security vulnerabilities:
* [CVE-2016-1669](http://www-01.ibm.com/support/docview.wss?uid=swg21986383)

## June 22, 2016: Updated Node.js buildpack v3.5-20160609-1608

This release of the buildpack adds IBM SDK for Node.js runtime versions 4.4.5 and 6.2.0. The default becomes 4.4.5.

The release removes support for older runtime versions as announced in [{{site.data.keyword.Bluemix_notm}} Node.js Buildpack v3.3 – FIPS mode and more](https://developer.ibm.com/bluemix/2016/05/05/node-buildpack-update-fips-mode/). The buildpack now supports 0.10.44, 0.10.45, 0.12.13, 0.12.14, 4.4.4, 4.4.5, 6.1.0, and 6.2.0.

This release includes bug fixes from the [Cloud Foundry’s Node.js buildpack 1.5.14](https://github.com/cloudfoundry/nodejs-buildpack/tree/v1.5.14).

## May 20, 2016: Updated Node.js buildpack v3.4-20160518-1653

This release of the buildpack adds IBM SDK for Node.js runtime versions 0.10.45, 0.12.14, 4.4.4, 6.0.0, and 6.1.0. The default is now 4.4.4.

Included are fixes for the following security vulnerabilities:
* [CVE-2015-8855](http://www-01.ibm.com/support/docview.wss?uid=swg21982852)
* [CVE-2016-2108 CVE-2016-2107 CVE-2016-2105 CVE-2016-2106 CVE-2016-2109 CVE-2016-2176 ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.openssl.org/news/secadv/20160503.txt)

Note that there is a known issue with npm v3 and the App Management inspector utility. npm 3.8.6 is the default with the 6.0.0 and 6.1.0 runtimes. If you want to use either of the 6.x runtimes and the inspector utility, you should specify a 2.x npm version in your package.json as a temporary workaround.

## April 29, 2016: Updated Node.js buildpack v3.3-20160428-1409

This release of the buildpack adds IBM SDK for Node.js runtime versions 0.10.44, 0.12.13, 4.4.0, 4.4.1, 4.4.2, and 4.4.3. The default is now 4.4.3.
i
For 4.3.1 and up, it is now possible to use a FIPS-enabled version of the runtime by setting the `FIPS_MODE=true` environment variable for your app.

The updated buildpack and the new runtime versions also contain fixes for security vulnerabilities:
* [CVE-2016-2515](http://www-01.ibm.com/support/docview.wss?uid=swg21977578)
* [CVE-2016-2537](http://www-01.ibm.com/support/docview.wss?uid=swg21977578)
* [CVE-2016-3956](http://www-01.ibm.com/support/docview.wss?uid=swg21980827)

The updated buildpack also contains fixes for several bugs:
* Now IBM SDK for Node.js builds will always be used if one is available matching the requested range. Previously, this case was only true for 4.x runtime versions.
* Now the App Management inspector utility will work with 4.x runtime versions.
* Fixed a regression in the strongpm App Management utility.

## March 18, 2016: Updated Node.js buildpack v3.2-20160315-1257

This release of the buildpack moves the default IBM SDK for Node.js runtime from version 4.3.0 to 4.3.2. It also includes IBM SDK for Node.js versions 0.10.43, 0.12.12, and 4.3.1. Use these recent Node.js versions to pick up fixes for several security vulnerabilities.

## March 4, 2016: Updated Node.js buildpack v3.1-20160222-1123

This release of the buildpack moves the default IBM SDK for Node.js runtime from version 4.2.4 to 4.3.0. It also includes IBM SDK for Node.js versions 0.10.42, 0.12.10, and 4.2.6. Use these recent Node.js versions to pick up fixes for several security vulnerabilities.

## February 4, 2016: Updated Node.js buildpack v3.0-20160125-1224

This release is fully synchronized with the [Cloud Foundry community Node.js](https://github.com/cloudfoundry/nodejs-buildpack) buildpack. In addition to community changes, modifications were made to certain defaults, along with optimizations to reduce staging time and updates to the App Management feature.

* Buildpack updates:

  * Node.js v4.2.4 (IBM SDK for Node.js Version 4) is now the default runtime on {{site.data.keyword.Bluemix_notm}}, replacing v0.12.9. This change might cause your application to behave differently if a particular version is not specified for your application. To learn how to specify a version of Node.js for your {{site.data.keyword.Bluemix_notm}} application, see [Node.js runtime](index.html) documentation.

  * NODE_ENV is now set to *production* by default. This change will cause some node dependencies to behave differently. For example, the Express framework will no longer return stacktraces in the web browser for faulty endpoints, but instead displays *Internal Server Error*. When NPM_CONFIG_PRODUCTION is set to *true*, NPM will set NODE_ENV to *production* for subshell scripts in the npm install phase only. This function allows users to set NODE_ENV to another value like *development* for application runtime. For clarity, npm scripts will see the message **NODE_ENV=production**.

  * A Bug-fix to the Monitoring and Analytics service is included.

* Caching updates:

  * If cache is disabled (NODE_MODULES_CACHE=false) the buildpack will not attempt to cache any modules/components. Previously this setting made it so that the cache is not popped, but it would still cache the installed modules for future deploys. Now, it will not pop the cache or attempt to store any cache.

  * Bower_components are cached by default in addition to node_modules.

* Other updates:

  * Added Helpful warnings for missing dependencies like gulp, bower, and angular.

  * The detect script is updated with buildpack version information.

  * The clustering recommendation (WEB_CONCURRENCY) initially introduced by community is removed as memory determination was inaccurate on {{site.data.keyword.Bluemix_notm}}.


## December 16, 2015: Updated Node.js buildpack v2.8-20151209-1403 and v3.0beta-20151211-2041

This release of the Node.js buildpack comes with two versions, v2.8 and v3.0beta. Both these versions include the following changes:

A Bug-fix to Monitoring and Analytics service
The inclusion of a cached runtime for IBM SDK for Node.js v4.2.3.0, v4.2.2.0, v1.2.0.8 and v1.2.0.7, which are based on community versions Node.js v4.2.3, v4.2.2, v0.12.9 and v0.12.8.
In addition, in v3.0beta the default Node.js runtime is changed to v4.2.3.

IBM Node.js buildpack v3.0beta is now released as a non-default buildpack on {{site.data.keyword.Bluemix_notm}} with Node.js v4.2.3 as the default runtime. To ensure that your apps and services will continue to work on {{site.data.keyword.Bluemix_notm}}, push your application with the beta version of the buildpack. After 30 days or longer, v3 will be made the default buildpack.

To push your application with v3.0beta:
* Use "-b" option in your `ibmcloud cf push` command:

```
        ibmcloud cf push -b sdk-for-nodejs-v3beta
```
{: codeblock}

* Or use the "buildpack" option in your manifest.yml file:

```
        buildpack: sdk-for-nodejs-v3beta
```
{: codeblock}

This change to the default runtime will not affect your application if you configured a specific version of Node.js in your application's package.json.

You can always specify the version of Node.js to run your application by using the engines.node entry in your package.json as explained in [Available versions](index.html#available_versions).
{: note}

## November 23, 2015: Updated Node.js buildpack v2.7-20151118-1003

With 2.7, version 4.2.1.0 of the IBM SDK for Node.js (based on Node v4.2.1 LTS) is included. It is not the default yet, but can be specified for use. **Note:** This version replaces the open source build that was previously available. We also made some small bug fixes to our service extension framework.

## October 19, 2015: Updated Node.js buildpack v2.6.1-20151015-1326

Node.js v2.6.1 introduces a bug fix to the [StrongPM app management handler](https://developer.ibm.com/bluemix/2015/10/15/strongloop-devops-on-bluemix/), and a more consistent NPM version.

## October 15, 2015: Updated Node.js buildpack v2.6-20151006-1309

This release of the Node.js buildpack features the integration of [StrongLoop Process Manager ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://strong-pm.io) to the App Management feature. For more information, see the blog post [StrongLoop DevOps for Node.js Applications on {{site.data.keyword.Bluemix_notm}}](https://developer.ibm.com/bluemix/2015/10/15/strongloop-devops-on-bluemix/).

## June 15, 2015: Updated Node.js buildpack v2.0-20150608-1503

In this release, we synced our Node.js buildpack with the latest [CF community Node.js buildpack](https://github.com/cloudfoundry/nodejs-buildpack), which comes with a number of new features from the community.
In addition, we revamped the App Management feature in the Node.js buildpack, which enables utilities like shell, node-inspector, {{site.data.keyword.Bluemix_notm}} Live Sync, and more. See [App Management](../common/app_mng.html) for details.

## May 5, 2015: Updated Node.js buildpack v1.17-20150429-1033

* The Node.js buildpack now comes with [IBM SDK for Node.js v0.12.1](https://developer.ibm.com/node/sdk/).
* If your application doesn’t specify a runtime in its package.json file, your app will now start by using v0.12.1, instead of v0.10.x. If you need to use the previous version, specify v0.10.x in your package.json as shown.

```
        "engines": {
            "node": "0.10.x"
        }
```
{: codeblock}

* Known issues with v0.12.1:
   * The "Suspend" feature is broken when you use the Debug Tools feature provided by {{site.data.keyword.Bluemix_notm}} Live Sync.
   * The mqlight module that is used for the MQ Light service is not supported on v0.12.x

* Various security vulnerabilities were resolved:
  * Fixed vulnerabilities in OpenSSL affecting IBM SDK for Node.js. More details are available in the [security bulletin](http://www-01.ibm.com/support/docview.wss?uid=swg21701494).
  * Fixed vulnerability in RC4 Stream Cipher affecting IBM SDK for Node.js. More details are available in the [security bulletin](http://www-01.ibm.com/support/docview.wss?uid=swg21882778).

##  April 2, 2015: Updated Node.js buildpack v1.15-20150331-2231

* The Node.js buildpack now includes three new features to help quickly develop on {{site.data.keyword.Bluemix_notm}} as you would on the desktop, without redeploying
  * Desktop Sync: Synchronize any (Windows) desktop tree to a cloud-based project workspace
  * Live Edit: Allows you to make changes to a Node.js application that runs in {{site.data.keyword.Bluemix_notm}} and test them in your browser right away.
  * Debug: Shell into your environment and debug! You can edit code dynamically, insert breakpoints, step through code, restart the runtime, and more by using the Node Inspector debugger
  * See [App Management](../common/app_mng.html#Utilities) for more information.
* We pulled in the latest changes from the [Cloud Foundry’s Node.js buildpack](https://github.com/cloudfoundry/nodejs-buildpack). This change comes with a number of bug-fixes and improvements made by the community.
* The Node.js buildpack now comes with [IBM SDK for Node.js v1.1.0.13](https://developer.ibm.com/node/sdk/).

## January 5, 2015: Updated Node.js buildpack v1.9.1-20141208-1221

* The Node.js buildpack now includes dynamic log setting support. With this support, developers can change the log level of their application dynamically if the application is using log4js, bunyan, or ibm{{site.data.keyword.Bluemix_notm}} modules for logging.
* The Node.js buildpack now comes with [IBM SDK for Node.js v0.10.33](https://developer.ibm.com/node/sdk/). This update includes fixes for the POODLE issue.

## October 23, 2014: Updated Node.js buildpack v1.6-20141013-1736

* The Node.js buildpack now comes with [IBM SDK for Node.js v1.1.0.8](https://developer.ibm.com/node/sdk/). This update means you get a fully supported IBM Node.js runtime when you specify the latest stable Node.js runtime for your application, v0.10.32. This latest SDK comes with a fix for an issue with the embedded qs module that resulted in a denial-of-service. It also contains an updated version of the npm module and other improvements in the http and url modules. For more details, see the [v0.10.32 Change Log](https://raw.githubusercontent.com/joyent/node/v0.10.32/ChangeLog).
* The buildpack also contains a fix for a bug that was adding an incorrect index.html file in the customer’s application during deployment.

## September 30, 2014: Updated Node.js buildpack v1.4-20140908-1746

* The Node.js buildpack now comes with [IBM SDK for Node.js v1.1.0.7](https://developer.ibm.com/node/sdk/). This update means that you get a fully supported IBM Node.js runtime when you specify the latest stable Node.js runtime for your application, v0.10.31. With a fully supported Node.js runtime, the customers receive a consistent support experience.
* The buildpack contains an improved service framework. Specifically, it works better when binding the Monitoring and Analytics service and provides more diagnostic information if the service fails.

## August 28, 2014: Updated Node.js buildpack v1.3-20140821-1143

* The newest Node.js buildpack now comes with IBM SDK for Node.js v1.1.0.6. This update means you will get a fully supported IBM Node.js runtime when you specify the latest stable Node.js runtime, v0.10.30, for your application. This runtime fixes the [V8 Memory Corruption vulnerability ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://blog.nodejs.org/2014/07/31/v8-memory-corruption-stack-overflow).
* The buildpack also includes improvements and bug fixes to the Monitoring and Analytics service extension, allowing you to diagnose performance and error conditions through the service.

## July 29, 2014: Updated Node.js buildpack v1.1-20140717-1447

The Node.js buildpack now comes with IBM SDK for Node.js v1.1.0.5. This update means you'll get a fully supported IBM Node.js runtime when you specify the latest stable Node.js runtime for your application, v0.10.29. See more about the [IBM Node.js SDKs](https://developer.ibm.com/node/sdk/).
