# SSH Forwarding

## Diagram

```bash
----    ----    --------
|PC| => |VM| => |Server|
----    ----    --------

pc@192.168.101.130:22 => vm@192.168.101.145:22 => server@192.168.10.13:22
```

## SSH Jump

```bash
ssh -J vm@192.168.101.145 server@192.168.10.13
```

## SSHFS Jump

```bash
sshfs -o ProxyCommand="ssh -W %h:%p vm@192.168.101.145" server@192.168.10.13:/home/server/Desktop /home/vm/Desktop/LAN/SERVER
```

## Port Mapping on Localhost e.g., 3000

```bash
ssh -L 3000:192.168.10.13:3000 vm@192.168.101.145

# On localhost web browser
http://localhost:3000

# On localhost terminal
telnet localhost 3000

# On localhost terminal
ssh server@localhost -p 3000
```
