---
tags:
  - Scraper
  - Resource Discovery
  - Data
  - Caching
  - Open Source
---

# Azure Cache for Redis Enterprise

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.6-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure Cache for Redis Enterprise via the `RedisEnterpriseCache` resource
type.

When using declared resources, the following fields need to be provided:

- `cacheName` - The name of the Azure Cache for Redis Enterprise resource

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftcacheredisenterprise).

## Example

Here is an example configuration:

```yaml
name: azure_cache_redis_enterprise_percentage_cpu
description: "Average percentage cpu usage on an Azure Cache for Redis Enterprise"
resourceType: RedisEnterpriseCache
azureMetricConfiguration:
  metricName: usedmemorypercentage
  aggregation:
    type: Average
resources: # Optional, required when no resource discovery is configured
- cacheName: promitor-redis-enterprise-cache-1
- cacheName: promitor-redis-enterprise-cache-2
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
- name: redis-enterprise-cache-landscape
```
