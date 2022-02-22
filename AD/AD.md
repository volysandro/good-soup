# How does AD work

## Ressources
- [https://medium.com/@adam.toscher/top-...](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqa3JZazg5YU5fWU1IRmlHZGJzdVlwOW1JbWE5QXxBQ3Jtc0tuc0hfYTVUV3NQbERkWlhfc0xoNVpqMjFCWjN4aHZScWFkV1hqN240LU1Rb1g3M3BvMkszNFQ4M25iaTIyekR3RzBUbFhVV0lxa3MyaGx3aENjQjZSeTRCZ0pZMWg2aVhMazNNTTkxbko0d0tfY3FIQQ&q=https%3A%2F%2Fmedium.com%2F%40adam.toscher%2Ftop-five-ways-i-got-domain-admin-on-your-internal-network-before-lunch-2018-edition-82259ab73aaa) 
- [https://adsecurity.org/](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbEZBVmFqTV9zUXRUNWNnQ29HSDZ5Q3AwczRnQXxBQ3Jtc0trOC1zd212UnFZeDNCXzhtLUpPS2doeGVGcTdhUGh0d05nN3BjOXlEaHdjMld1YWRRVlZ0WjU5QXNCQ2dwaFpQeVhXeGdhaVg0ZGo1R3pENjFDNDJpMU9IQnpFNk53TXdTVkk4TDBhZHdPVXhuZk1abw&q=https%3A%2F%2Fadsecurity.org%2F) 
- [https://blog.harmj0y.net/](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbGtjQTFTRkdpZXhGbVdrbDIxS251Wk1lYjRwUXxBQ3Jtc0tta2stSnpWQk9iYzVZb0VqamFGUHc4b29idTRMblN6cHdZMUltczAxZ1R3cXdjZFRaTHRSSXAzWV91SHlvNEk4VDhRSkp2RVk1eVlvQlFsYXNubmlfdGR2aU11Y25ubDN3Nk9aVHlBTDFjQXVycVBFbw&q=https%3A%2F%2Fblog.harmj0y.net%2F) 
- [https://blog.g0tmi1k.com/2011/08/basi...](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbExvOTk0am91LU9JaXM5elZFWXI4TUdGS21qd3xBQ3Jtc0tsbnpodzV2bzBFdmJXOW5aRmxaT0ktb0JuVVRtVUp1OTJQV2ZLYkM2czJWVU5PT1JMc2xhLWR1M0VjVU9HbFlwUzQ1SGZfeUtrMUpabVZKQkdpLUFEWlduYzdBV3pwQmU4cVhkODluYkpwVzJsXzJxUQ&q=https%3A%2F%2Fblog.g0tmi1k.com%2F2011%2F08%2Fbasic-linux-privilege-escalation%2F)  - [https://www.fuzzysecurity.com/tutoria...](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqa2Z6a2FEMVdBMHBfbmNORzNqdnFuZHZXZ2dUQXxBQ3Jtc0ttWkx6MFF3SGxlN3hQYlR5Z3hYaTVGOEdpMm5MMUJsQnZrdXYyUXN6RnNGME5vZTY3WDhTMG9LZ2JSZGFzUDlHYjBQSVJoU3J6ZU9KUkVUTFpGeVE1V1YyM0xCZ24ycWloM0ZGRmlNOGVYM2VFOWJKYw&q=https%3A%2F%2Fwww.fuzzysecurity.com%2Ftutorials%2F16.html)

## Basics
 - Basic AD user can enumerate anything within AD
 - DC = Domain Controller -> Most important role, windows server, Active Directory Domain Services installed
 - Forest: Added 2003, allows separate domains under same umbrella
 - Hierarchical, forest is on top
 - Forest can contain multiple domains, a domain may include further child or sub domains
 - Domain is a structure within objects (users, computers, groups) are accessible


## Basic Structure
### Forest
At the top, likely the root domain
### Domains
A forest can contain one or more domains
A domain is a structure which contains objects (users, computers, groups)
A domain has built in organizational units (OU) (Domain Controllers, Users, Computers)
New OUs can be created as required

### Organizational Unit (OU)
May contain objects and sub-OUs

### Child and Subdomains
Each domain in itself can contain further child and subdomains

### Trust Relationships
Trust relationships can be used between domains to perform acquisitions. It's quicker than recreating users in the current domain.
Domain trusts can introduce security issues.

Trusts can be bi-directional and trusting a root domain would mean that all child domains are trusted. 
This does NOT apply vice versa, a child domain can not necessarily access another child domain of a trusted root forest.

## Terminology
### Object
An object can be ANY ressource within an AD environment.
For example:
 - Organizational Units
 - Printers
 - Users
 - Domain Controllers

### Attributes
Every object in an AD has a set of [attributes](https://docs.microsoft.com/en-us/windows/win32/adschema/attributes-all).
A computer object could contain hostname and DNS name attributes.
All attributes have an associated LDAP name for LDAP queries:
 - displayName = Full Name
 - given name = First Name

### Schema
The schema is essentialy the blueprint for an environment.
it defines:
 - What types of objects can exist + associated attributes
 - Definitions to AD objects: "user" class for users, computers get class "computer"
Each object has own information stored in attributes.
Creating object from class: instantation
Object from class: instance of class
Computer RDS01 could be instance of "computer" class

### Domain
Think of each domain as a different city, operate independently or be connected with trust relationships.
Group of objects such as computers, users, OUs, groups, etc.

### Forest
Topmost container, contains all AD objects. Think of a forest as the state within a country. Can operate independently or be connected with trust relationships.

### Tree
Tree = collection of AD domains which begins at a single root domain. A forest is a collection of trees. Two trees in the same forest cannot share a name. parent-child trust relationship is formed when a domain is added under a domain in a tree. All domains in a tree share a standard Global Catalog which contiains information about objects in a tree.

### Container
A container can hold objects

### Global Unique Identifier (GUID)
A GUID is a 128-bit value assigned when a user or group is created. This value is unique across the enterprise (similar to MAC address). Every single object created by AD is assigned a GUID.
GUID is stored in ObjectGUID attribute. Searching AD by GUID is the most accurate and reliable way to find an exact object. ObjectGUID property never changes while the object exists in the domain.

### Security Principals
In AD, security principals are domain objects that can manage access to other ressources within the domain. This is possible locally as well, but is managed by the Security Accounts Manager (SAM).

### Security Identifier (SID)
A SID is used as a unique identifier for a security principal or security group. Every account, group, or process has its own unique SID, which is issued by the domain controller and stored in a secure database.
A SID can only be used once. 
On login, a user receives a token which contains it's SID, the permissions granted and the SID of every group the user is a member of. This token is used to check rights when the user performs actions.
There is also [well-known SIDs](https://ldapwiki.com/wiki/Well-known%20Security%20Identifiers), like the "Everyone" group.

### Distinguished Name (DN)
A [DN](https://docs.microsoft.com/en-us/previous-versions/windows/desktop/ldap/distinguished-names) describes the full path to an object in AD.
cn=Common Name -> one way the user object could be searched for
ou=Organizational Unit -> eg. IT or Employyees
dc=Domain Component -> A part of domain name to search for ? can be multiple

### Relative Distinguished Name (RDN)
Other than the distinguished name (DN), RDN is only a single component of the DN which is unique within the organizational unit. For example, the common name would be a Relative Distinguished Name because it is the unique identifier relative to the rest of the DN. Unix ldap systems mostly use uid instead of commonname to distinguish, so there that could be the RDN relative to the whole query. 

TLDR; RDN is the final part of the DN which searchs for the specific object in the given DN

### sAMAccountName
the sAMAccountName is the users logon name. Must be a unique value and 20 or fewer characters.




