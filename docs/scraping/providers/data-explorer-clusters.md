---
tags:
  - Scraper
  - Resource Discovery
  - Data
---

# Azure Data Explorer Clusters

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.0-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure Data Explorer Cluster via the `DataExplorerCluster` resource
type.

When using declared resources, the following fields need to be provided:

- `clusterName` - The name of the Azure Data Explorer Cluster

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftkustoclusters).

## Example

Here is an example configuration:

```yaml
name: azure_data_explorer_cluster
description: "CPU usage of Azure Data Explorer cluster"
resourceType: DataExplorerCluster
azureMetricConfiguration:
  metricName: CPU
  aggregation:
    type: Average
resources: # Optional, required when no resource discovery is configured
- clusterName: promitor-data-explorer-cluster-1
- clusterName: promitor-data-explorer-cluster-2
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://promitor.io/concepts/how-it-works#using-resource-discovery)
- name: data-explorer-cluster-landscape
```
