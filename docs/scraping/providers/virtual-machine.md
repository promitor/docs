---
tags:
  - Scraper
  - Resource Discovery
  - IaaS
---

# Azure Virtual Machine (VM)

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v1.0-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure Virtual Machine via the `VirtualMachine` resource
type.

When using declared resources, the following fields need to be provided:

- `virtualMachineName` - The name of the virtual machine

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftcomputevirtualmachines).

## Example

Here is an example configuration:

```yaml
name: azure_virtual_machine_percentage_cpu
description: "Average percentage cpu usage on an Azure virtual machine"
resourceType: VirtualMachine
azureMetricConfiguration:
  metricName: Percentage CPU
  aggregation:
    type: Average
resources: # Optional, required when no resource discovery is configured
- virtualMachineName: promitor-virtual-machine-1
- virtualMachineName: promitor-virtual-machine-2
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
- name: virtual-machine-landscape
```
