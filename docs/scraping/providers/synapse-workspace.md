---
tags:
  - Scraper
  - Resource Discovery
  - Data
  - Synapse
---

# Azure Synapse (Workspace)

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.1-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can scrape an Azure Synapse workspace via the `SynapseWorkspace` resource type.

When using declared resources, the following fields need to be provided:

- `workspaceName` - The name of the Azure Synapse workspace.

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftsynapseworkspaces).

The following scraper-specific metric labels will be added:

- `workspace_name` - The name of the Azure Synapse workspace.

## Example

Here is an example configuration:

```yaml
- name: promitor_demo_synapse_workspace_builtin_sql_processed_bytes
  description: "Amount of bytes processed in Azure Synapse workspace"
  resourceType: SynapseWorkspace
  azureMetricConfiguration:
    metricName: BuiltinSqlPoolDataProcessedBytes
    aggregation:
      type: Total
  resources: # Optional, required when no resource discovery is configured
  - workspaceName: promitor-synapse
    resourceGroupName: promitor-sources
  resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
  - name: synapse-workspaces
```
