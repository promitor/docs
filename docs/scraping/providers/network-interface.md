---
tags:
  - Scraper
  - Resource Discovery
  - Networking
---

# Azure Network Interface

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v1.0-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an [Azure Network Interface](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-network-interface)
via the `NetworkInterface` resource type.

When using declared resources, the following fields need to be provided:

- `networkInterfaceName` - The name of the network interface

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftnetworknetworkinterfaces).

## Example

Here is an example configuration:

```yaml
name: azure_network_interface_bytes_received_rate
description: "Number of bytes the Network Interface sent"
resourceType: NetworkInterface
azureMetricConfiguration:
  metricName: BytesReceivedRate
  aggregation:
    type: Average
resources: # Optional, required when no resource discovery is configured
- networkInterfaceName: promitor-network-interface-1
- networkInterfaceName: promitor-network-interface-2
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
- name: network-interfaces-landscape
```
