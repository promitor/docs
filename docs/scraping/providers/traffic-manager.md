---
tags:
  - Scraper
  - Resource Discovery
  - Networking
---

# Azure Traffic Manager Profile

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.9-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape a Traffic Manager via the `TrafficManager` resource type.

When using declared resources, the following fields need to be provided:

- `name` - The name of the Traffic Manager Profile.

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftnetworktrafficmanagerprofiles).

## Example

Here is an example configuration:

```yaml
name: azure_traffic_manager_endpoint_qps
description: "Number of times a Traffic Manager endpoint was returned in the given time frame"
resourceType: TrafficManager
azureMetricConfiguration:
  metricName: QpsByEndpoint
  aggregation:
    type: Total
resources: # Optional, required when no resource discovery is configured
- name: promitor-traffic-manager
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
- name: traffic-managers
```
