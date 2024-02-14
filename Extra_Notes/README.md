# Extra Notes

- #### Metasploit persistent listen on incoming reverse shells :
  - When you generate your payload, do add `exitonsession=false` as flags next to lhost and lport
  - On multi/handler, do also `set exitonsession false` and start listening with `run -j`
  
----
