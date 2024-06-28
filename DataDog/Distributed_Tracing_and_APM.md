## Importance of APM and **Distributed Tracing**

Modern applications are often built as distributed systems composed of multiple services that group together web endpoints, database queries, or other resources that support the application.

When a request is made to a service in a distributed system, oftentimes the service hits multiple downstream services to process the request. If a service fails or performs poorly while processing the request, it’s important to pinpoint the root cause of the problem. And, with more than one service involved in processing a request, pinpointing the root cause becomes a challenge. Application performance monitoring (APM) in Datadog brings together your application trace data, related infrastructure metrics, and log data so that you can understand and troubleshoot your application’s performance at all levels.

With [**Datadog APM**](https://docs.datadoghq.com/tracing/), you can solve the following issues and more:

1. Find traces matching a bug report for a customer, status code, and endpoint
2. Live view your application trace data to gain performance insights at a glance
3. Identify the slowest SQL queries on a database for a specific host and shard
4. View slow and cold-starting serverless functions

Datadog APM employs distributed tracing to optimize your application performance monitoring. Distributed tracing allows you to track the progress and status of a request as it is handled by your application’s distributed system. You can also live query all traces and only keep the ones you need.

### Distributed Traces and Spans

In distributed tracing, when a request is made to an application, a trace is created that collects performance data from each service involved in processing the request. The trace is made up of spans. Each span represents an operation or logical unit of work performed by a service in response to the request. Services that perform more than one operation to handle the request produce a span for each operation.

Traces are typically visualized as flame graphs. The flame graph below shows a trace for a request made to the `Admin::ProductsController#update` endpoint of the web-store service of an application. The starting point for the top span is the time the endpoint receives the request. The top span has two child spans because the request is handled by calling on two other resources: a database query to the web-store-mongo service and a second operation by the `Admin::ProductController#update` endpoint of a web-store service. In this instance, the web-store service has a dependency on the web-store-mongo service.

![Flame graph of a trace with 3 spans](https://files.cdn.thinkific.com/file_uploads/655405/images/928/050/2b0/01-01_flamegraph.png)

The length of each span represents the duration of each operation involved in completing the request. Each span has a name that describes the operation, a start time, a duration, and span tags.

Span tags are key:value pairs that describe the infrastructure, application, and business dimensions of each span. In Datadog, span tags can be automatically assigned through [**integration inheritance**](https://docs.datadoghq.com/getting_started/tagging/assigning_tags/?tab=noncontainerizedenvironments#integration-inheritance), [**instrumentation**](https://docs.datadoghq.com/tracing/guide/metrics_namespace/), or [**manually assigned**](https://docs.datadoghq.com/getting_started/tagging/assigning_tags/?tab=noncontainerizedenvironments#configuration-file) as custom tags. A tag can be specific to certain spans or global to all spans in a service or application. For example, you can assign customer and merchant tags to ecommerce application data (indicated in the image below).

![Examples of custom span tags for customer and merchant](https://files.cdn.thinkific.com/file_uploads/655405/images/93c/368/a89/01-02_traceview_customermerchanttags.png)

Datadog has [**reserved tag keys**](https://docs.datadoghq.com/tagging/#introduction) for correlating metric, trace, and log data throughout the platform. If you assign any of these tags, use them only for the purposes listed below.

![List of reserved tag keys used to correlate specific metric, trace, and log data throughout Datadog: host, device, source, service, env, and version](https://files.cdn.thinkific.com/file_uploads/655405/images/d29/895/8d5/01-03_reversedtags_docs_updated.png)

The reserved keys `env`, `service`, and `version`, specifically, can be used for unified service tagging of containerized and non-containerized environments. [**Unified service tagging**](https://docs.datadoghq.com/getting_started/tagging/unified_service_tagging/?tab=kubernetes) allows you to scope application data across metrics, logs, and traces by version in addition to environment and service, so that you can observe the behavior of different versions of services deployed over time.

To learn more about tagging best practices in Datadog, you can view the [**Tagging documentation**](https://docs.datadoghq.com/getting_started/tagging/) and the [**Tagging Best Practices course**](https://learn.datadoghq.com/courses/tagging-best-practices).

### Traces in Datadog

In Datadog APM, you can search your application traces in Traces Search and Live Search, and you can view the details of traces in the Trace View.

**[Traces Search](https://docs.datadoghq.com/tracing/app_analytics/search/)** - Traces Search allows you to search the traces that have been sampled and indexed by the Datadog backend based on the span tags. Datadog employs a [**trace sampling strategy**](https://docs.datadoghq.com/tracing/guide/trace_sampling_and_storage/?tab=java#trace-sampling) that keeps the traces that matter most, including the following:

1. Distributed traces
2. Traces from low queries-per-second (qps) services
3. Traces corresponding to bad user experiences such as errors
4. Traces corresponding to high latencies or failed requests
5. The variety of traces representative of the distributed system

In Traces Search, you can use the search field and the Facets on the left (in image below) to filter traces as needed.

![Traces Search of shop.ist environment](https://files.cdn.thinkific.com/file_uploads/655405/images/89e/405/003/01-04_trace-search.png)

**[Live Search](https://docs.datadoghq.com/tracing/livetail/)** - Live Search allows you to search all trace spans ingested by the Datadog Agent in near real time.

![Live Search of shop.ist environment](https://files.cdn.thinkific.com/file_uploads/655405/images/75a/756/5f4/01-05_trace-live.png)

**[Trace View](https://docs.datadoghq.com/tracing/visualization/trace/?tab=spantags)** - In Trace View, each trace is visualized as a Flame Graph and a Span List. The first span is the span for the resource that receives the request—meaning, the trace will be listed in the page for that resource. The Span List is a table visualization of the Flame Graph. Tags and any correlated infrastructure, host metrics, logs, errors, runtime metrics, and processes are also listed for each span in the trace.

![Trace View of web-store service trace](https://files.cdn.thinkific.com/file_uploads/655405/images/d6b/8c6/db7/01-06_trace-view.png)

### App Instrumentation for Datadog APM

Before you can monitor your application’s performance using Datadog, you need to configure the Datadog Agent to receive traces and instrument the application services.

[**Agent Configuration**](https://docs.datadoghq.com/tracing/send_traces/) - Datadog supports multiple methods to receive traces through the Datadog Agent. This can be done locally, from containers, using serverless, and through other environments like Heroku and Cloud Foundry.

[**Application Instrumentation**](https://docs.datadoghq.com/tracing/setup/) - Datadog provides tracing libraries/clients for automatic instrumentation for a variety of languages: Java, Python, Ruby, C++, Go, Node.js, .NET, .NET Core, PHP, Envoy, Nginx, and Istio.

You can also [**manually instrument**](https://docs.datadoghq.com/tracing/manual_instrumentation/) your app for tracing in-house code not captured by automatic instrumentation and for deeper visibility and context into spans, including assigning any custom span tags.

In the following hands-on activity, you will instrument an ecommerce application for Datadog APM.

# Correlate Logs and Traces

[Docs](https://docs.datadoghq.com/) &gt; [APM](https://docs.datadoghq.com/tracing/) &gt; [Correlate APM Data with Other Telemetry](https://docs.datadoghq.com/tracing/other_telemetry/) &gt; [Correlate Logs and Traces](https://docs.datadoghq.com/tracing/other_telemetry/connect_logs_and_traces/)

![Logs in Traces](https://datadog-docs.imgix.net/images/tracing/connect_logs_and_traces/trace_id_injection.32c00c69e59d6c50e6c89efc16b27af3.png?fit=max&auto=format)

The correlation between Datadog APM and Datadog Log Management is improved by the injection of trace IDs, span IDs, `env`, `service`, and `version` as attributes in your logs. With these fields, you can find the exact logs associated with a specific service and version, or all logs correlated to an observed [trace](https://docs.datadoghq.com/tracing/glossary/#trace).

It is recommended to configure your application’s tracer with `DD_ENV`, `DD_SERVICE`, and `DD_VERSION`. This will provide the best experience for adding `env`, `service`, and `version`. See the [unified service tagging](https://docs.datadoghq.com/getting_started/tagging/unified_service_tagging) documentation for more details.

Before correlating traces with logs, ensure your logs are either sent as JSON or [parsed by the proper language level log processor](https://docs.datadoghq.com/agent/logs/#enabling-log-collection-from-integrations). Your language level logs *must* be turned into Datadog attributes in order for traces and logs correlation to work.
