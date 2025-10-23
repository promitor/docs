---
tags:
  - Scraper
  - Resource Discovery
  - Networking
  - DNS
---

# Azure DNS Zone

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.5-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure DNS Zone via the `DnsZone` resource type.

When using declared resources, the following fields need to be provided:

- `zoneName` - The name of the DNS zone

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/supported-metrics/microsoft-network-dnszones-metrics).

## Example

Here is an example configuration:

```yaml
name: azure_dns_zone_capacity_utilization
description: "Percentage of record set capacity utilized by a DNS zone"
resourceType: DnsZone
scraping:
  schedule: "0 */2 * ? * *"
azureMetricConfiguration:
  metricName: RecordSetCapacityUtilization
  aggregation:
    type: Maximum
    interval: 00:01:00
resources: # Optional, required when no resource discovery is configured
  - zoneName: promitor.io
  - zoneName: api.promitor.io
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
  - name: dns-zone-landscape
```
