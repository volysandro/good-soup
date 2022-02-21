# NTLM Authentication
## How does it work
- Client calculates NTLM hash
- Client sends username
- Server sends challenge
- Client encrypts challenge
- Server sends response, username and challenge to domain controller
- Domain controller encrypts challenge with NTLM hash of user and compares to response
- Domain controller approves the authentication

