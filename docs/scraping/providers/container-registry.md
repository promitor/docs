---
tags:
  - Scraper
  - Resource Discovery
  - Containers
---

# Azure Container Registry

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v1.0-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure Container Registry via the `ContainerRegistry`
resource type.

When using declared resources, the following fields need to be provided:

- `registryName` - The name of the registry

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftcontainerregistryregistries).

## Example

Here is an example configuration:

```yaml
name: azure_container_registry_total_pull_count
description: "Amount of images that were pulled from the container registry"
resourceType: ContainerRegistry
azureMetricConfiguration:
  metricName: TotalPullCount
  aggregation:
    type: Average
resources: # Optional, required when no resource discovery is configured
- registryName: promitor-1
- registryName: promitor-2
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
- name: container-registry-landscape
```
