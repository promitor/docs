---
tags:
  - Scraper
  - Resource Discovery
  - Networking
---

# Azure Load Balancer

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.6-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure Load Balancer via the `LoadBalancer` resource
type.

When using declared resources, the following fields need to be provided:

- `loadBalancerName` - The name of the Azure Load Balancer resource

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftnetworkloadbalancers).

## Example

Here is an example configuration:

```yaml
name: azure_load_balancer_traffic_bytes
description: "Average amount of bytes sent through an Azure Load Balancer"
resourceType: LoadBalancer
azureMetricConfiguration:
  metricName: ByteCount
  aggregation:
    type: Average
resources: # Optional, required when no resource discovery is configured
- loadBalancerName: promitor-load-balancer-1
- loadBalancerName: promitor-load-balancer-2
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
- name: load-balancer-landscape
```
