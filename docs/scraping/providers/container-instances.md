---
tags:
  - Scraper
  - Resource Discovery
  - Containers
---

# Azure Container Instances

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v1.0-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure Container Instances via the `ContainerInstance`
resource type.

When using declared resources, the following fields need to be provided:

- `containerGroup` - The name of the container group

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftcontainerinstancecontainergroups).

## Example

Here is an example configuration:

```yaml
name: azure_container_instance_cpu_usage
description: "Average cpu usage of our 'promitor-container-instance' container instance"
resourceType: ContainerInstance
azureMetricConfiguration:
  metricName: CpuUsage
  aggregation:
    type: Average
resources: # Optional, required when no resource discovery is configured
- containerGroup: promitor-container-instance-1
- containerGroup: promitor-container-instance-2
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
- name: container-instances-landscape
```
