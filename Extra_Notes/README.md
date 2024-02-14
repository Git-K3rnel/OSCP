# Extra Notes

- #### Metasploit persistent listen on incoming reverse shells :
  ```
  1. When you generate your payload, do add "exitonsession=false" as flags next to lhost and lport
    
  2. On multi/handler, do also "set exitonsession false" and start listening with "run -j"
  ```
----
