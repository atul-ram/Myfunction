```
resources
| where type =~ 'microsoft.network/virtualNetworks'
| extend number = array_length(properties.virtualNetworkPeerings)
| where number < 3
```

```
resources
| where type =~ 'Microsoft.Databricks/workspaces'
| mv-expand uri = (properties.workspaceUrl)
| project name, strcat("https://", uri, "/")
```