---
tags:
  - Scraper
  - Resource Discovery
  - Networking
---

# Azure Front Door

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.1-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure Front Door via the `FrontDoor` resource
type.

When using declared resources, the following fields need to be provided:

- `name` - The name of the Azure Front Door

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftnetworkfrontdoors).

## Example

Here is an example configuration:

```yaml
name: promitor_demo_frontdoor_backend_health
description: "Health percentage for backends in Azure Front Door"
resourceType: FrontDoor
azureMetricConfiguration:
  metricName: BackendHealthPercentage
  aggregation:
    type: Average
resources: # Optional, required when no resource discovery is configured
- name: promitor-landscape
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
- name: front-door-landscape
```
