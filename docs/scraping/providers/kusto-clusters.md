---
tags:
  - Scraper
  - Resource Discovery
  - Data
---

# Azure Kusto Clusters

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.0-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure Kusto Cluster via the `KustoCluster` resource
type.

When using declared resources, the following fields need to be provided:

- `kustoClusterName` - The name of the Azure Kusto Cluster

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftkustoclusters).

## Example

Here is an example configuration:

```yaml
name: azure_kusto_cluster
description: "CPU usage of Azure kusto cluster"
resourceType: KustoCluster
azureMetricConfiguration:
  metricName: CPU
  aggregation:
    type: Average
resources: # Optional, required when no resource discovery is configured
- kustoClusterName: promitor-kusto-cluster-1
- kustoClusterName: promitor-kusto-cluster-2
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://promitor.io/concepts/how-it-works#using-resource-discovery)
- name: kusto-cluster-landscape
```
