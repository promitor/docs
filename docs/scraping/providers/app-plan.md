---
tags:
  - Scraper
  - Resource Discovery
  - PaaS
  - Web
  - API
---

# Azure App Plan

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v1.2-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure App Plan via the `AppPlan` resource
type.

When using declared resources, the following fields need to be provided:

- `appPlanName` - The name of the Azure App Plan

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftwebserverfarms).

## Example

Here is an example configuration:

```yaml
name: azure_app_plan_percentage_memory
description: "Average percentage of memory usage on an Azure App Plan"
resourceType: AppPlan
azureMetricConfiguration:
  metricName: MemoryPercentage
  aggregation:
    type: Average
resources: # Optional, required when no resource discovery is configured
- appPlanName: promitor-app-plan
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
- name: app-plans-landscape
```
