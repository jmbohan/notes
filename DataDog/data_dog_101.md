# Datadog #
## Universal Service Monitoring (USM) ##

The Service Catalog is a centralized place to view all services in your application


## Datadog Log Management ##

allows you to cost-effectively collect, process, archive, explore, and monitor all your logs without limitations.

The **Log Explorer** is your central hub for investigating and exploring logs

A search query in Log Explorer is composed of terms (either a single word or a group of words surrounded by double quotes) and Boolean operators. You can also filter logs using log facets, which are user-defined tags and attributes from your indexed logs, which are logs that have been collected, processed, and retained for analysis, alerting, and troubleshooting.

- Live tail (in the time range drop down menu) provides visibility into all logs, whether they are indexed or not. This is useful if you want to check if a process has correctly started or if a new deployment has gone smoothly.

To the left of the log list, there is a facet panel

Common tags and attributes automatically appear in the facet panel as Datadog parses logs. Facets are useful for qualitative or quantitative data analysis, so you can use them to search through logs, define log patterns, and perform log analytics. Although the automatically generated facets are helpful, you might also want to create your own custom facet that appears in the facet panel. You can accomplish this with the help of the log details in the log side panel    


## Metrics ##

**Metrics** are the smallest unit in the Datadog universe but they grant enormous insight into your infrastructure when they are visualized, measured, and monitored. Metrics are numerical measurements about any aspect of your system over a period of time, such as latency, error rates, or user registrations. In Datadog, metric data is received and retained as data points that include a value and timestamp

**Monitors** send notifications when metrics fall outside of the tolerances that you define.


**Service** Level Objectives track metrics over long periods of time to help you define quality standards.

### Metric Monitors ###

Monitors will continuously check metrics, integration availability, network endpoints, and other vital aspects for conditions that you define. When a threshold is exceeded, Datadog will notify you or your team on the Datadog mobile app, by email, or on your chat platform. This capability is essential for complete infrastructure visibility in one centralized location.

Datadog offers a variety of monitors to cater to different monitoring needs. Some of the most popular types of monitors include:

**Metric monitors**: Used to track and alert on specific metrics. This type of monitor is commonly used to track things like server CPU usage, memory utilization, or network bandwidth. For example, Send a notification to the DevOps team if average HTTP response time exceeds 1.50 seconds.

**Service Checks**: Used to verify the status and availability of various services, such as databases or APIs. Service Checks can be used to monitor both external and internal services. For example, is the redis service healthy?

**APM monitors**: Used to monitor application performance, track errors, and measure latency. This monitor provides insights into how applications are executing and helps to identify potential issues. For example, alert the development team with an application’s Errors per second is above 25.

**Synthetics monitors**: Used to monitor critical user flows and business transactions. Synthetic API tests and browser tests help you proactively identify issues in application endpoints and key business workflows before your end users encounter them. Synthetics monitors can simulate user actions, such as logging in or adding an item to a shopping cart, and alert you if there are any errors or delays.

**Log monitors**: Used to monitor specific keywords or patterns in log data. Log monitors can track security issues, application errors, or system events.

- The evaluation graph is specific to the monitor. It uses the same query logic as the history graph, but it is scoped to the timeframe bracket on the history graph. It has a fixed, zoomed window that corresponds to your monitor evaluation window to ensure the displayed points are aggregated correctly.

## Service Level Objectives ## 

SLOs enable you to set clear performance targets for a delivered service, product, or application—and then measure how well you are meeting these targets over time. In Datadog, you use SLOs to determine whether a performance measurement (or set of measurements) has been meeting a minimum threshold for a target percentage of time (by default, 99.9%) over a rolling time window of 7, 30, or 90 days. This capability lets you track how well your organization is meeting its service obligations with its external customers or internal end users.

## Integrations ##

The Datadog Agent is software that runs on your hosts. It collects process- level events and metrics and sends them to Datadog, where you can analyze your monitoring and performance data. For this course, the Datadog Agent has already been installed for you in all the labs.

Every organization has its own, unique infrastructure. For the most part, the Datadog Agent’s default core integrations cover the most common attributes of these infrastructures—disk, CPU, memory, network throughput, etc. However, it’s possible to tailor Datadog to your specific infrastructure by either utilizing community integrations or creating your integration.

There are three main types of integrations: Agent-based, authentication-based, and library. You can even build your own integration!

- **Agent-based integrations** are installed with the Datadog Agent (on your host or in containers) and use a Python class method called check to define the metrics to collect.

- **Authentication (crawler) based** integrations are set up in Datadog where you provide credentials to obtain metrics and data from APIs. These include popular integrations like Slack, AWS, Azure, and PagerDuty.

- **Library integrations** use the Datadog API to allow you to monitor applications based on the language they’re written in, like Node.js or Python.

The Agent-based and authentication-based integrations offer an array of new metrics and pre-configured dashboards, whereas library integrations are imported into your application code to monitor your application logs, traces, and custom metrics. All the integrations and instructions for installing them are easily accessible in the Datadog app.

In the following hands-on activity, you will observe:

- an Agent-based integration that’s already installed and running in the lab environment
- the installed integrations and out-of-the-box (OOTB) dashboards in the Datadog app
- third-party integrations and the data they collect

**Note**: Every integration **Configuration** tab has an **Uninstall Integration** button at the bottom, should you need it. This will uninstall the integration only from Datadog, not the Agent. To fully remove an Agent integration, you must run the Agent's `integration remove` command.


## Dashboards ##

Dashboards are persistent, sharable arrangements of graphs and other visuals called widgets.

