---
tags:
  - Scraper
  - Resource Discovery
  - Networking
---

# Azure Private Link Service

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.16-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure Private Link Service via the `PrivateLinkService` resource type.

When using declared resources, the following fields need to be provided:

- `privateLinkServiceName` - The name of the Azure Private Link Service

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/supported-metrics/microsoft-network-privatelinkservices-metrics).

## Example

Here is an example configuration:

```yaml
name: azure_private_link_service_bytes_in
description: "Total number of bytes in for an Azure Private Link Service"
resourceType: PrivateLinkService
azureMetricConfiguration:
  metricName: PLSBytesIn
  aggregation:
    type: Total
resources: # Optional, required when no resource discovery is configured
- privateLinkServiceName: promitor-private-link-service-1
- privateLinkServiceName: promitor-private-link-service-2
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
- name: private-link-service-landscape
```