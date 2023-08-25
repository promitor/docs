---
tags:
  - Scraper
  - Resource Discovery
  - PowerBI
  - PowerBI Embedded
---

# Azure PowerBI Dedicated

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.11-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape a PowerBi Dedicated capacity via the `PowerBiDedicated` resource-type.

When using declared resources, the following fields need to be provided:

- `capacityName` - The name of the PowerBI Dedicated capacity

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/supported-metrics/microsoft-powerbidedicated-capacities-metrics).

## Example

Here is an example configuration:

```yaml
  - name: azure_powerbi_dedicated_cpu_usage
    description: percentage of cpu used by powerbi dedicated
    resourceType: PowerBidedicated
    azureMetricConfiguration:
        metricName: cpu_metric
        aggregation:
            type: Average
    resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
        - name: powerbi-dedicated
```
