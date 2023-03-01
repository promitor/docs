---
tags:
  - Scraper
  - Resource Discovery
  - SQL
  - Data
  - Open Source
---

# Azure Database for PostgreSQL

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v1.0-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure Database for PostgreSQL server via the `PostgreSql`
resource type.

When using declared resources, the following fields need to be provided:

- `serverName` - The name of the PostgreSQL server
- `type` - The type of PostgreSQL server. *(optional)*
  - Allowed values are `Simple` (default), `Flexible` & `Hyperscale`.

All supported metrics are documented in the official Azure Monitor documentation:

- [Simple servers](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftdbforpostgresqlservers)
- [Flexible servers](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftdbforpostgresqlflexibleservers)
- [Hyperscale servers](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftdbforpostgresqlservergroupsv2)

## Limitations

- Resource discovery will discover all types of servers and thus the used metrics should match all of the types.
  - You can use tags to define which resources to include, if you need filtering capabilities.

## Example

Here is an example configuration:

```yaml
name: azure_postgre_sql_cpu_percent
description: "The CPU percentage on the server"
resourceType: PostgreSql
scraping:
  schedule: "0 */2 * ? * *"
azureMetricConfiguration:
  metricName: cpu_percent
  aggregation:
    type: Average
    interval: 00:01:00
resources: # Optional, required when no resource discovery is configured
- serverName: Promitor-1
- serverName: Promitor-2
  type: Flexible
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
- name: postgres-database-landscape
```
