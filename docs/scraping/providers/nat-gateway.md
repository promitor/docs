---
tags:
  - Scraper
  - Resource Discovery
  - Networking
---

# Azure NAT Gateways

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.9-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure NAT Gateway via the `NatGateway` resource
type.

When using declared resources, the following fields need to be provided:

- `natGatewayName` - The name of the Azure NAT Gateway

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftnetworknatgateways).

## Example

Here is an example configuration:

```yaml
name: azure_nat_gateway_datapath_availability
description: "DatapathAvailability usage of Azure nat gateway"
resourceType: NatGateway
azureMetricConfiguration:
  metricName: DatapathAvailability
  aggregation:
    type: Average
resources: # Optional, required when no resource discovery is configured
- natGatewayName: promitor-nat-gateway-1
- natGatewayName: promitor-nat-gateway-2
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://promitor.io/concepts/how-it-works#using-resource-discovery)
- name: nat-gateway-landscape
```
