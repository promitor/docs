---
tags:
  - Scraper
  - Resource Discovery
  - Networking
---

# Azure Express Route Circuit

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.0-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure Express Route Circuit (without Peerings) via the `ExpressRouteCircuit` resource
type.

When using declared resources, the following fields need to be provided:

- `expressRouteCircuitName` - The name of the Azure Express Route circuit

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftnetworkexpressroutecircuits).

## Example

Here is an example configuration:

```yaml
name: azure_express_route_percentage_arp_availability
description: "Average percentage of arp availability on an Azure express route circuit"
resourceType: ExpressRouteCircuit
azureMetricConfiguration:
  metricName: ArpAvailability
  aggregation:
    type: Average
resources: # Optional, required when no resource discovery is configured
- expressRouteCircuitName: promitor-express-route-circuit-1
- expressRouteCircuitName: promitor-express-route-circuit-2
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
- name: express-route-circuit-landscape
```
