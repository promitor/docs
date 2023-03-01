---
tags:
  - Scraper
  - Resource Discovery
  - Data
  - Synapse
---

# Azure Synapse (SQL pool)

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.1-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can scrape an Azure Synapse SQL pool via the `SynapseSqlPool` resource type.

When using declared resources, the following fields need to be provided:

- `workspaceName` - The name of the Azure Synapse workspace.
- `poolName` - The name of the SQL pool.

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftsynapseworkspacessqlpools).

The following scraper-specific metric labels will be added:

- `workspace_name` - The name of the Azure Synapse workspace.
- `pool_name` - The name of the SQL pool.

## Example

Here is an example configuration:

```yaml
- name: promitor_demo_synapse_sql_pool_dwu_limit
  description: "Amount of DWUs defined as limit for SQL pool in Azure Synapse"
  resourceType: SynapseSqlPool
  azureMetricConfiguration:
    metricName: DWULimit
    aggregation:
      type: Maximum
  resources: # Optional, required when no resource discovery is configured
  - workspaceName: promitor-synapse
    poolName: sqlpool
  resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
  - name: synapse-sql-pools
```
