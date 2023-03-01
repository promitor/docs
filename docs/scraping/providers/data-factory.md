---
tags:
  - Scraper
  - Resource Discovery
  - Data
  - Integration
  - PaaS
---

# Azure Data Factory

![Availability Badge](https://img.shields.io/badge/Available%20Starting-v2.5-green.svg)![Resource Discovery Support Badge](https://img.shields.io/badge/Support%20for%20Resource%20Discovery-Yes-green.svg)

You can declare to scrape an Azure Data Factory resource via the `DataFactory` resource
type.

When using declared resources, the following fields need to be provided:

- `factoryName` - The name of the Azure Data Factory resource
- `pipelineName` - The name of the data pipeline *(optional)*

All supported metrics are documented in the official [Azure Monitor documentation](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-supported#microsoftdatafactoryfactories).

The following scraper-specific metric label will be added:

- `pipeline_name` - Name of the data pipeline.

## Example

Here is an example configuration:

```yaml
- name: azure_data_factory_pipeline_run_successful
  description: "Amount of successful runs for 'data-pipeline-example' pipline in Azure Data Factory"
  resourceType: DataFactory
  azureMetricConfiguration:
    metricName: PipelineSucceededRuns
    aggregation:
      type: Total
  resources: # Optional, required when no resource discovery is configured
  - factoryName: promitor-data-factory
    pipelineName: data-pipeline-example
  resourceDiscoveryGroups: # Optional, requires Promitor Resource Discovery agent (https://docs.promitor.io/latest/how-it-works#using-resource-discovery)
  - name: data-factory-landscape
```
