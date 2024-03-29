---
tags:
  - Scraper
  - Resource Discovery
  - SQL
  - Data
  - PaaS
---

# Azure SQL Database

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v1.1-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can scrape an Azure SQL Database via the `SqlDatabase` resource type.

When using declared resources, the following fields need to be provided:

- `serverName` - The name of the SQL Server instance.
- `databaseName` - The name of the database.

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftsqlserversdatabases).

The following scraper-specific metric labels will be added:

- `server` - The name of the SQL Server instance.
- `database` - The name of the database.

## Example

Here is an example configuration:

```yaml
name: azure_sql_database_dtu_consumption_percent
description: "The DTU consumption percentage used by an Azure SQL Database."
resourceType: SqlDatabase
azureMetricConfiguration:
  metricName: dtu_consumption_percent
  aggregation:
    type: Average
resources: # Optional, required when no resource discovery is configured
- serverName: promitor-sql-server
  databaseName: promitor-db
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
- name: sql-database-landscape
```
