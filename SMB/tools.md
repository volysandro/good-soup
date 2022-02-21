# Tools

## nmblookup
- Used to lookup NetBIOS names and map them to network
`nmblookup -A <host>`

## nbtscan
- queries NetBIOS status for each host and returns ip, hostname, user etc.

## nmap scripts
- `smb-os-discovery`
- `nbstat.nse`

## smbmap
- `smbmap -H ip`
- `smbmap -H ip -u username -p password`

## smbclient
- look for shares: `smbclient -N -L //ip`
- Download directory recursively:
````
smbclient '\\server\share' -N -c 'prompt OFF;recurse ON;cd 'path\to\directory\';lcd '~/path/to/download/to/';mget *'`
````


