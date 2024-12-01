# Declaring resource discovery groups

Promitor Resource Discovery allows you to declare the Azure landscape to explore and define resource discovery groups
 in YAML.

Resource discovery groups represent a group of Azure resources of a given type that can be scraped by Promitor Scraper
 and supports an extensive list of supported services.

As part of the resource discovery group declaration, you can choose to filter resources by adding inclusion criteria
 that resources must comply with based on:

- **Subscription** - Defines a subset of subscriptions defined in the Azure landscape
- **Resource Group** - Defines a list of resource groups which contains the resources.
- **Tags** - Defines a list of [Azure tags](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/tag-resources)
 with which the resources have to be annotated.
- **Regions** - Defines a list of Azure regions in which the regions the resources are located.

Here is an example of a full declaration:

```yaml
version: v1
azureLandscape:
  tenantId: e0372f7f-a362-47fb-9631-74a5c4ba8bbf
  subscriptions:
  - SUBSCRIPTON-ID-ABC
  - SUBSCRIPTON-ID-DEF
  - SUBSCRIPTON-ID-GHI
  cloud: China
resourceDiscoveryGroups:
- name: container-registry-landscape
  type: ContainerRegistry
- name: filtered-logic-apps-landscape
  type: LogicApp
  criteria:
    include:
      subscriptions:
      - SUBSCRIPTON-ID-ABC
      - SUBSCRIPTON-ID-GHI
      resourceGroups:
      - promitor-resource-group-1
      - promitor-resource-group-2
      tags:
        app: promitor-1|promitor-2
        region: europe
      regions:
      - northeurope
      - westeurope
```

## Specification

As Promitor evolves we need to change the structure of our resource discovery declaration.

`version: {version}` - Version of declaration that is used. Allowed
values are `v1`. *(Required)*

### Azure Landscape

- `azureLandscape.tenantId` - The id of the Azure tenant that will be queried. *(Required)*
- `azureLandscape.subscriptions` - List of Azure subscriptions in the Azure tenant to discover resources in. *(Required)*
- `azureLandscape.cloud` - The name of the Azure cloud to use. Options are `Global` (default), `China`, `UsGov` & `Germany`.

### Resource Discovery Groups

Every resource discovery group that is being declared needs to define the following fields:

- `name` - Name of the resource discovery group which will be used in metrics declaration of Promitor Scraper. *(Required)*
- `type` - Type of Azure resources that must be discovered, see "Supported Azure Services" for a full list of supported types. *(Required)*
- `criteria` - Criteria to fine-tune discovered resource.

#### Criteria

As of now, we only allow to define criteria that resources have to meet before they are included in the resource
 discovery group:

- `subscriptions` - A list of subscription(s) in which the resource is allowed to be located.
- `resourceGroups` - A list of resource group(s) in which the resource is allowed to be located.
- `tags` - A list of [Azure tags](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/tag-resources)
 and the expected values (exact or regular expression) with which the resources have to be annotated. (Uses `or`)
- `regions` - A list of Azure region(s) in which the resource is allowed to be located.
