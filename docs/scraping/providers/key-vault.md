---
tags:
  - Scraper
  - Resource Discovery
  - Security
---

# Azure Key Vault

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v1.6-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure Key Vault
via the `KeyVault` resource type.

When using declared resources, the following fields need to be provided:

- `vaultName` - The name of the Azure Key Vault

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftkeyvaultvaults).

## Example

Here is an example configuration:

```yaml
name: azure_key_vault_api_latency
description: "The overall latency of service api requests"
resourceType: KeyVault
azureMetricConfiguration:
  metricName: ServiceApiLatency
  aggregation:
    type: Average
resources: # Optional, required when no resource discovery is configured
- vaultName: promitor-1
- vaultName: promitor-2
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
- name: key-vault-landscape
```
