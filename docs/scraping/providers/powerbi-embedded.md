---
tags:
  - Scraper
  - Resource Discovery
  - PowerBi
---

# Azure PowerBi Embedded

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.9-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape a PowerBi Embedded capacity via the `PowerBiEmbedded` resource-type.

When using declared resources, the following fields need to be provided:

- `capacityName` - The name of the PowerBi Embedded capacity

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/supported-metrics/microsoft-powerbidedicated-capacities-metrics).

## Example

Here is an example configuration:

```yaml
  - name: azure_powerbi_embedded_cpu_usage
    description: percentage of cpu used by powerbi embedded
    resourceType: PowerBiEmbedded
    azureMetricConfiguration:
        metricName: cpu_metric
        aggregation:
            type: Average
    resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
        - name: powerbi-embedded
```
