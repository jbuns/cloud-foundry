---

copyright:
  years: 2015, 2018
lastupdated: "2018-12-12"
subcollection: cloud-foundry

---

{:new_window: target="_blank"}
{:codeblock: .codeblock}

# Use New Relic to monitor Liberty in {{site.data.keyword.cloud_notm}}
{: #new_relic}

New Relic is a third-party service that provides monitoring metrics for your application. For more information on what the New Relic service provides, see [New Relic](http://newrelic.com/java).

According to the [Java agent manual installation documentation](https://docs.newrelic.com/docs/agents/java-agent/installation/java-agent-manual-installation), Java applications that are to be monitored by using the New Relic service are typically required to be bundled and configured with a New Relic agent and an account license key. In the {{site.data.keyword.Bluemix}} environment, a New Relic license agreement and account can be obtained by creating a service instance in {{site.data.keyword.Bluemix_notm}}. Java applications can then be bound to the New Relic service instance and the Liberty buildpack auto configures the application that is ready to be monitored by the New Relic service.
Specifically, the buildpack:

* provides the application with a New Relic agent.
* obtains the application name and license key from the VCAP_APPLICATION and VCAP_SERVICES application environment variables.
* configures the properties and configuration template that is required by the New Relic agent.

See the sample configuration that is generated by the Liberty buildpack for the application:

```
    -javaagent:/home/vcap/app/.new_relic_agent/new_relic_agent-3.12.0.jar
    -Dnewrelic.home=/home/vcap/app/.new_relic_agent
    -Dnewrelic.config.license_key=123456
    -Dnewrelic.config.app_name=myapp
    -Dnewrelic.config.log_file_path=../../../../../logs
```
{: codeblock}


## Add a user-provided New Relic service
{: #add_user_provided_new_relic}

If you have an existing New Relic account and license key, you may bind the existing New Relic service to your application using a "user-provided service".

1. Create a user-provided service instance using your existing license key.  For example, if your existing license key is 1234567, you can use the {{site.data.keyword.Bluemix_notm}} CLI to "create-user-provided-service" and provide the license key 1234567 at the prompt as in the following:

  ```
    ibmcloud cf create-user-provided-service mynewrelic -p "licenseKey"
    licenseKey> 1234567
  ```
  {: codeblock}

2. Deploy your application to {{site.data.keyword.Bluemix_notm}} with the user-provided New Relic service instance.  The following
is a sample application manifest that uses a user-provided
New Relic service instance:
  <pre>
        &dash;&dash;&dash;
        applications:
        - name: myapp
         memory: 1G
         instances: 1
         host: myapp
         domain: mybluemix.net
         path: myapp.war
         services:
         - mynewrelic
  </pre>
  {: codeblock}

3. Access the New Relic dashboard to view the application metrics.

Auto configuration of the New Relic service is different from the auto configuration of other services as it is a container managed service that is made available through the buildpack's framework.  Since it is made available through the framework, the auto configuration for this service is different from the other services in three ways:
* Opting out is not an option.
* The service integration relies on New Relic's agent, a Java agent. Therefore, it is configured through Java options as opposed to cloud variables in the server.xml file.
* The configuration relies on both VCAP_SERVICES and VCAP_APPLICATION.