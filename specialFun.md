

```
Function Get-AgentIP {
    If (Get-Variable -Name cachedAgentIPAddress -Scope Global -ErrorAction SilentlyContinue) {
        Return $Global:cachedAgentIPAddress
    }
    Else {
        $agentIP = Invoke-WebRequestWithRetries -Uri "http://ipinfo.io/json" -Method Get | ConvertFrom-Json | Select-Object -ExpandProperty ip
        Write-Verbose "Determined public IP address of hosted agent: '$agentIP'."
        $Global:cachedAgentIPAddress = $agentIP
        Return $agentIP
    }
}
```
