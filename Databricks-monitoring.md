

DatabricksSecrets 
//| where ActionName !in ('getSecret', 'listSecrets','createScope')
| where ActionName in ('putSecret')
| extend SecretKey = extractjson('$key', RequestParams)
| extend SecretScope = extractjson('$scope', RequestParams)
| extend StatusCode = extractjson('$statusCode',Response)
| project TimeGenerated,ActionName,SecretKey,SecretScope,StatusCode
