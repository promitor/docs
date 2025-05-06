---
tags:
  - Scraper
  - Resource Discovery
  - Data
  - Caching
  - Open Source
---

# Azure Cache for Redis

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v1.0-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure Cache for Redis via the `RedisCache` resource
type.

When using declared resources, the following fields need to be provided:

- `cacheName` - The name of the Redis Cache instance

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftcacheredis).

You can find more documentation on each metric in the Azure Cache for Redis
[monitoring documentation](https://learn.microsoft.com/en-us/azure/azure-cache-for-redis/cache-how-to-monitor#available-metrics-and-reporting-intervals).

## Example

Here is an example configuration:

```yaml
name: azure_redis_cache_cache_hits
description: "The number of successful key lookups during the specified reporting interval. This maps to keyspace_hits from the Redis INFO command."
resourceType: RedisCache
scraping:
  schedule: "0 */2 * ? * *"
azureMetricConfiguration:
  metricName: CacheHits
  aggregation:
    type: Total
    interval: 00:01:00
resources: # Optional, required when no resource discovery is configured
- cacheName: Promitor-1
- cacheName: Promitor-2
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
- name: redis-cache-landscape
```
