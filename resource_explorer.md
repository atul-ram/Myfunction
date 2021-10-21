resources
| where type =~ 'microsoft.network/virtualNetworks'
| extend number = array_length(properties.virtualNetworkPeerings)
| where number < 3
