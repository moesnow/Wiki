# Frp

> https://github.com/fatedier/frp

### frps

```frps
[common]
bind_port = 
authenticate_new_work_conns = true
authentication_method = token
token = 
```

### frpc

```frpc
[common]
server_addr = 
server_port = 
authenticate_new_work_conns = true
authentication_method = token
token = 


[ssh]
type = tcp
local_ip = 127.0.0.1
local_port = 22
remote_port = 
```
