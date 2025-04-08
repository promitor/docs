---
tags:
  - Scraper
  - Resource Discovery
  - Cognitive Services Accounts
---

# Cognitive Services

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.12-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can scrape an Cognitive Service Accounts via the `CognitiveServicesAccounts`
resource type.

When using declared resources, the following fields need to be provided:

- `cognitiveServicesAccountsName` - The name of the Cognitive Services Accounts.

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/supported-metrics/microsoft-cognitiveservices-accounts-metrics).

## Example

Here is an example configuration:

```yaml
name: cognitive_services_rate_limit
description: The current ratelimit of the ratelimit key.
resourceType: CognitiveServicesAccounts
azureMetricConfiguration:
  metricName: Ratelimit
  aggregation:
    type: Count
  dimension:
    name: Status
resourceDiscoveryGroups:
  - name: cognitive-services-accounts
```
