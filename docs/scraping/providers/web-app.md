---
tags:
  - Scraper
  - Resource Discovery
  - PaaS
---

# Azure Web App

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v1.2-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure Web App via the `WebApp` resource
type.

When using declared resources, the following fields need to be provided:

- `webAppName` - The name of the Azure Web App
- `slotName` - The name of the deployment slot *(optional)*

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftwebsites-excluding-functions).

The following scraper-specific metric label will be added:

- `slot_name` - Name of the deployment slot. If none is specified, `production` will be used.

Example:

```yaml
name: azure_web_app_requests
description: "Amount of requests for an Azure Web App"
resourceType: WebApp
azureMetricConfiguration:
  metricName: Requests
  aggregation:
    type: Total
resources: # Optional, required when no resource discovery is configured
- webAppName: promitor-web-app
  slot: staging
- webAppName: promitor-web-app
  slot: production
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
- name: web-app-landscape
```
