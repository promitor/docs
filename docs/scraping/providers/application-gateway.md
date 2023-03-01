---
tags:
  - Scraper
  - Resource Discovery
  - Networking
---

# Azure Application Gateway

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.0-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure Application Gateway via the `ApplicationGateway` resource
type.

When using declared resources, the following fields need to be provided:

- `applicationGatewayName` - The name of the Azure Application Gateway

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftnetworkapplicationgateways).

## Example

Here is an example configuration:

```yaml
name: azure_application_gateway_milli_total_time
description: "Average milliseconds of total time on an Azure application gateway"
resourceType: ApplicationGateway
azureMetricConfiguration:
  metricName: ApplicationGatewayTotalTime
  aggregation:
    type: Average
resources: # Optional, required when no resource discovery is configured
- applicationGatewayName: promitor-application-gateway-1
- applicationGatewayName: promitor-application-gateway-2
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
- name: application-gateway-landscape
```
