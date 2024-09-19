---
tags:
  - Scraper
  - Resource Discovery
  - Azure Firewall
---

# Azure Automation account

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.1-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can scrape an Azure Automation account via the `AzureFirewall`
 resource type.

When using declared resources, the following fields need to be provided:

- `azureFirewallName` - The name of the Azure Firewall.

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/supported-metrics/microsoft-network-azurefirewalls-metrics).


## Example

Here is an example configuration:


```yaml
name: azure_firewall_application_rule_hits
description: number of times Application rules were hit	
resourceType: AzureFirewall
azureMetricConfiguration:
  metricName: ApplicationRuleHit
  aggregation:
    type: Count
  dimension:
    name: Status
resourceDiscoveryGroups:
  - name: azure-firewalls
```