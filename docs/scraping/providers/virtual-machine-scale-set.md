---
tags:
  - Scraper
  - Resource Discovery
  - IaaS
---

# Azure Virtual Machine Scale Set (VMSS)

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v1.2-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure Virtual Machine Scale Set via the `VirtualMachineScaleSet` resource
type.

When using declared resources, the following fields need to be provided:

- `scaleSetName` - The name of the Virtual Machine Scale Set

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftcomputevirtualmachinescalesets).

## Example

Here is an example configuration:

```yaml
name: azure_virtual_machine_scale_set_percentage_cpu
description: "Average percentage cpu usage on an Azure virtual machine scale set"
resourceType: VirtualMachineScaleSet
azureMetricConfiguration:
  metricName: Percentage CPU
  dimension:
    name: VMName
  aggregation:
    type: Average
resources: # Optional, required when no resource discovery is configured
- scaleSetName: promitor-virtual-machine-scale-set-1
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
- name: virtual-machine-scale-sets-landscape
```
