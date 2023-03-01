---
tags:
  - Scraper
  - Resource Discovery
  - Networking
---

# Azure Network Gateway

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.0-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure Network Gateway via the `NetworkGateway` resource
type.

When using declared resources, the following fields need to be provided:

- `networkGatewayName` - The name of the Azure Network Gateway

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftnetworkvirtualnetworkgateways).

## Example

Here is an example configuration:

```yaml
name: azure_network_gateway_packages
description: "Average packages on an Azure network gateway"
resourceType: NetworkGateway
azureMetricConfiguration:
  metricName: ExpressRouteGatewayPacketsPerSecond
  aggregation:
    type: Average
resources: # Optional, required when no resource discovery is configured
- networkGatewayName: promitor-network-gateway-1
- networkGatewayName: promitor-network-gateway-2
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
- name: network-gateway-landscape
```
