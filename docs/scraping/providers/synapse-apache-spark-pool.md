---
tags:
  - Scraper
  - Resource Discovery
  - Data
  - Synapse
---

# Azure Synapse (Apache Spark pool)

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.1-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can scrape an Azure Synapse Apache Spark pool via the `SynapseApacheSparkPool` resource type.

When using declared resources, the following fields need to be provided:

- `workspaceName` - The name of the Azure Synapse workspace.
- `poolName` - The name of the Apache Spark pool.

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftsynapseworkspacesbigdatapools).

The following scraper-specific metric labels will be added:

- `workspace_name` - The name of the Azure Synapse workspace.
- `pool_name` - The name of the Apache Spark pool.

## Example

Here is an example configuration:

```yaml
- name: promitor_demo_synapse_apache_spark_apps_ended
  description: "Amount of apps ended running on Apache Spark pool in Azure Synapse"
  resourceType: SynapseApacheSparkPool
  azureMetricConfiguration:
    metricName: BigDataPoolApplicationsEnded
    aggregation:
      type: Total
  resources: # Optional, required when no resource discovery is configured
  - workspaceName: promitor-synapse
    poolName: sparkpool
  resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
  - name: synapse-apache-spark-pools
```
