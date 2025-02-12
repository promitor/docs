# Frequently asked questions (FAQs)

Here are a list of questions you may have:

- [Are multi-dimensional metrics supported?](#are-multi-dimensional-metrics-supported)
- [How does Promitor handle deleted resources?](#how-does-promitor-handle-deleted-resources)
- [Is scraping multiple subscriptions supported?](#is-scraping-multiple-subscriptions-supported)
- [What Azure clouds are supported?](#what-azure-clouds-are-supported)
- [Why does Azure Blob & File Storage only report account-level information?](#why-does-azure-blob-file-storage-only-report-account-level-information)
- [Why does my multi-dimensional metric report label value `unknown` with Prometheus?](#why-does-my-multi-dimensional-metric-report-label-value-unknown-with-prometheus)
- [What operating systems are supported?](#what-operating-systems-are-supported)

## Are multi-dimensional metrics supported?

Yes, every scraper supports scraping multi-dimensional metrics except for
Azure Storage queues.

You can configure the dimension(s) you are interested in via
`azureMetricConfiguration.dimensions`, for more information see
our ['Metrics Declaration' page](scraping/overview.md#metrics).

However, you can only use it with metrics in Azure Monitor that support this,
for a complete overview we recommend reading the
[official documentation](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/metrics-supported).

## How does Promitor handle deleted resources?

The approach depends if you are using declarative metrics or resource discovery but we highly recommend to
 **enable Prometheus metric timestamps** in [our runtime configuration](scraping/runtime-configuration.md#prometheus-scraping-endpoint)
  to indicate how old the metric is.

### When using declarative metrics

Promitor will scrape all resources that are configured and report the metrics accordingly. If that resource is deleted,
 we will **still serve the metrics as long as we can until it is no longer available and exceptions will be thrown**.

We **recommend to update the metrics declaration when a resource is deleted** to avoid polluting logs.

### When using resource discovery

Promitor will automatically discover all matching resources which means that **it will automatically scrape metrics for
 new/removed resources**.

Removed resources will immediately stop being scraped by Promitor, but still be reported in Prometheus scrape endpoint.

## Is scraping multiple subscriptions supported?

No, we do not support scraping multiple subscriptions as of today as we consider that to be a security boundary.

However, you can deploy multiple instances of Promitor that each scrape another subscription.

We have it on [our backlog](https://github.com/tomkerkhove/promitor/issues/761) to see if there is
 enough demand for it, feel free to give a :+1:. If that is the case, we will reconsider this limitation.

## What Azure clouds are supported?

We support `Global` (default), `China`, `UsGov`, `Germany` & `Custom` Azure clouds.

This can be configured in the metric configuration under `azureMetadata` and in resource discovery configuration under `azureLandscape`

For more information see our ['Metric Configuration' page](scraping/overview.md) and [`Resource Discovery` page](resource-discovery/declaring-resource-discovery-groups.md).

## Why does Azure Blob & File Storage only report account-level information?

Azure Monitor currently only provides account-level metrics which we can serve.

As part of [#450](https://github.com/tomkerkhove/promitor/issues/450) &
 [#446](https://github.com/tomkerkhove/promitor/issues/446) we plan to provide the capability to have more granular information.

## Why does my multi-dimensional metric report label value `unknown` with Prometheus?

When Promitor is unable to find a metric for a multi-dimensional metric, it will report `unknown` for the dimension
 label given it was not able to determine what the dimension value is due to the lack of metrics.

You can read more about it in our [Prometheus sink documentation](scraping/runtime-configuration.md#what-happens-when-metrics-are-unavailable-for-multi-dimensional-metrics).

## What operating systems are supported?

We support running on both Linux & Windows platforms.
