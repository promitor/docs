---
tags:
  - Scraper
  - Resource Discovery
  - IoT
  - PaaS
---

# Azure IoT Hub

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v1.6-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure IoT Hub via the `IoTHub` resource type.

When using declared resources, the following fields need to be provided:

- `ioTHubName` - The name of the Azure IoT Hub

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftdevicesiothubs).

## Example

Here is an example configuration:

```yaml
name: azure_iot_hub_total_devices
description: "The number of devices registered to your IoT hub"
resourceType: IoTHub
azureMetricConfiguration:
  metricName: devices.totalDevices
  aggregation:
    type: Total
resources: # Optional, required when no resource discovery is configured
- ioTHubName: promitor-1
- ioTHubName: promitor-2
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
- name: iot-hub-landscape
```
