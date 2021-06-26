
```
DatabricksSecrets 
//| where ActionName !in ('getSecret', 'listSecrets','createScope')
| where ActionName in ('putSecret')
| extend SecretKey = extractjson('$key', RequestParams)
| extend SecretScope = extractjson('$scope', RequestParams)
| extend StatusCode = extractjson('$statusCode',Response)
| project TimeGenerated,ActionName,SecretKey,SecretScope,StatusCode
```
```
DatabricksAccounts 
| extend user = extractjson('$user', RequestParams)
| extend tokenId = extractjson('$tokenId', RequestParams)
| extend StatusCode = extractjson('$statusCode',Response)
| project TimeGenerated, ActionName,user,tokenId,StatusCode
```
