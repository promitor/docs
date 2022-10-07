---
tags:
  - Scraper
  - Data
---

# Azure Log Analytics

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.9-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-No-red.svg)

You can declare to scrape an Azure Log Analytics via the `LogAnalytics` resource type.

The following fields need to be provided:

- `name` - The name of the Azure Log Analytics
- `workspaceId` - The workspaceId of the Log Analytics

LogAnlaytics is different resource compare to others azure metric. So you need to replace azureMetricConfiguration field with logAnalyticsConfiguration field:

- `logAnalyticsConfiguration.query` - The query used to query value from logAnalytics
    - the result of the query need to be 1 row only (use `take 1`)
    - the result of the query need to have 1 column named 'result' only (use `project result`)
- `logAnalyticsConfiguration.aggregation.interval` - The aggregation that needs to be
  used when querying Log Analytics. If you don't set this, it will get the value from metricDefaults

## Example

Here is an example configuration:

```yaml
name: azure_logs_analytics
description: "Get number of error from SparkLoggingEvent"
resourceType: LogAnalytics 
logAnalyticsConfiguration:
  query: SparkLoggingEvent_CL | where Level == "ERROR" | summarize result = count() | take 1 | project result
  aggregation:
    interval: 10:00:00:00
resources:
  - workspaceId: 0202fe93-55de-4c08-ae83-b5e4a3b6bed6
    name: afs-log-analytics
```