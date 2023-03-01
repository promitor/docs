---
tags:
  - Scraper
  - Resource Discovery
  - IoT
  - PaaS
---

# Azure IoT Hub Device Provisioning Service (DPS)

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v1.6-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure IoT Hub Device Provisioning Service (DPS)
via the `DeviceProvisioningService` resource type.

When using declared resources, the following fields need to be provided:

- `deviceProvisioningServiceName` - The name of the Azure IoT Hub Device Provisioning Service (DPS)

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftdevicesprovisioningservices).

## Example

Here is an example configuration:

```yaml
name: azure_dps_attestation_attempts
description: "The number of device attestations attempted"
resourceType: DeviceProvisioningService
azureMetricConfiguration:
  metricName: AttestationAttempts
  aggregation:
    type: Total
resources: # Optional, required when no resource discovery is configured
- deviceProvisioningServiceName: promitor-1
- deviceProvisioningServiceName: promitor-2
resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
- name: iot-hub-dps-landscape
```
