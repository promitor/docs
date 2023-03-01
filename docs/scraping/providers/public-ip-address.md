---
tags:
  - Scraper
  - Resource Discovery
  - Networking
---

# Azure Public IP Address

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.9-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape a Public IP Address via the `PublicIpAddress`
resource type.

When using declared resources, the following fields need to be provided:

- `publicIpAddressName` - The name of the Public IP Address.

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftnetworkpublicipaddresses).

## Example

Here is an example configuration:

```yaml
name: azure_public_ip_address_under_ddos_attack
description: "Public IP Address under DDoS attack or not"
resourceType: PublicIpAddress
azureMetricConfiguration:
  metricName: IfUnderDDoSAttack
  aggregation:
    type: Maximum
resources: # Optional, required when no resource discovery is configured
- publicIpAddressName: promitor-load-balancer-public-ip
- publicIpAddressName: promitor-nat-gateway-public-ip
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
- name: public-ip-address-landscape
```
