---
tags:
  - Scraper
  - Resource Discovery
  - Integration
  - Messaging
---

# Azure Service Bus Namespace

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.0-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure Service Bus namespace via the `ServiceBusNamespace`
resource type.

When using declared resources, the following fields need to be provided:

- `namespace` - The name of the Azure Service Bus namespace
- `queueName` - The name of the queue *(optional)*
- `topicName` - The name of the topic *(optional)*

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftservicebusnamespaces).

The following scraper-specific metric label will be added:

- `entity_name` - Name of the queue

## Limitations

- No support for `queueName` & `topicName` for the same resource, for example:

```yaml
resources:
- namespace: promitor-messaging
  queueName: orders
  topicName: sales
```

- No support for combining the `queueName` & `EntityPath` dimensions

## Example

Here is an example configuration:

<!-- markdownlint-disable MD046 -->
```yaml
name: azure_service_bus_queue_active_messages
description: "The number of active messages on a service bus queue"
resourceType: ServiceBusNamespace
azureMetricConfiguration:
  metricName: ActiveMessages
  aggregation:
    type: Total
resources: # Optional, required when no resource discovery is configured
- namespace: promitor-messaging
  queueName: orders
- namespace: promitor-messaging
  queueName: items
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
- name: service-bus-landscape
```
<!-- markdownlint-enable -->
