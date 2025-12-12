---
tags:
  - Scraper
  - Resource Discovery
  - DocumentDB
  - MongoDB
  - Database
  - Open Source
---

# Azure DocumentDB MongoCluster

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.15-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can scrape an Azure DocumentDB MongoCluster via the `MongoCluster` resource type.

When using declared resources, the following fields need to be provided:

- `clusterName` - The name of the MongoDB cluster.

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/supported-metrics/microsoft-documentdb-mongoclusters-metrics).

## Example

Here is an example configuration:

```yaml
name: azure_mongo_cluster_cpu_percent
description: "CPU utilization percentage for MongoDB cluster"
resourceType: MongoCluster
azureMetricConfiguration:
  metricName: CpuPercent
  aggregation:
    type: Average
resources: # Optional, required when no resource discovery is configured
  - clusterName: my-mongo-cluster-1
  - clusterName: my-mongo-cluster-2
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent
  - name: mongo-cluster-landscape
```

## Additional Examples

### Memory Utilization

```yaml
name: azure_mongo_cluster_memory_percent
description: "Memory utilization percentage for MongoDB cluster"
resourceType: MongoCluster
azureMetricConfiguration:
  metricName: MemoryPercent
  aggregation:
    type: Average
resources:
  - clusterName: my-mongo-cluster
```

### Request Duration

```yaml
name: azure_mongo_cluster_request_duration
description: "Request duration in milliseconds for MongoDB cluster"
resourceType: MongoCluster
azureMetricConfiguration:
  metricName: MongoRequestDurationMs
  aggregation:
    type: Average
resources:
  - clusterName: my-mongo-cluster
```

### Storage Utilization

```yaml
name: azure_mongo_cluster_storage_percent
description: "Storage utilization percentage for MongoDB cluster"
resourceType: MongoCluster
azureMetricConfiguration:
  metricName: StoragePercent
  aggregation:
    type: Average
resources:
  - clusterName: my-mongo-cluster
```
