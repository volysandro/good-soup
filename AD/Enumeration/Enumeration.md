# AD Enumeration
## Enumeration
- Covers mostly enumeration *after* initial foothold, credentials or shell is required

### With creds
#### The Linux way
- `GetADUsers.py -all -dc-ip 10.10.10.110 domain.com/username`

#### The Windows way
##### net.exe
- enumerating local accounts
Examples:
```
net user
net user /domain
net user <username> /domain
net group
net group /domain

```

#### Currently logged on users
- Use *PowerView.ps1*
- `Import-Module .\PowerView.ps1`
- `Get-NetLoggedon -ComputerName <name>`
- `Get-NetSession -ComputerName <dc-name>`

#### Service Principal Names
Services that are run on Windows, are launched by the system itself through service accounts. *LocalSystem*, *LocalService*, and *NetworkService*. When Applications (Exchange, SQL, IIS, etc.) are installed in AD, a Service Principal Name is used to associate the service to a service account.

- Use script to discover *serviceprincipalname*s
- `nslookup <SPN`
- Will return the ip address, likely of domain controller


