# Scenario 1
## Set up share
- Goto: Server Manager -> File and Storage Services -> Shares
- Top right "TASKS" -> Create new share
- "Share Quick"
- Custom location -> New folder "hackme" -> C:\ drive
- Enable "permission based access"
- Create

## Add share to Windows Client
- Open Explorer
- "This PC" -> "Computer" -> "Map network drive"
- Drive: Z, Folder: '\\HYDRA\hackme'

## Test
- Create a file and vice versa lol


Continue in [[llmnr_nbt-ns_poisoning]]