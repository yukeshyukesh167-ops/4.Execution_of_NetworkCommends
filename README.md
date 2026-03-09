# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>

## Client.py:
```
import socket

s = socket.socket()
s.connect(("localhost", 8000))

while True:
    ip = input("Enter the website you want to ping: ")
    s.send(ip.encode())
    print(s.recv(1024).decode())
```
## Server.py:
```
import socket
from pythonping import ping

s = socket.socket()
s.bind(("localhost", 8000))
s.listen(5)

print("Server started...")

c, addr = s.accept()
print("Connected to", addr)

while True:
    hostname = c.recv(1024).decode()

    if not hostname:
        break

    try:
        result = ping(hostname, verbose=False)
        c.send(str(result).encode())
    except Exception:
        c.send("Not Found".encode())
```
## Output

Server.py:

<img width="659" height="69" alt="Screenshot 2026-03-09 142140" src="https://github.com/user-attachments/assets/dd8fe96d-3c56-4a97-819d-ab7e4b036d69" />

Client.py:

<img width="653" height="129" alt="Screenshot 2026-03-09 141733" src="https://github.com/user-attachments/assets/05bd266b-e8a7-4d74-b881-5ea4da246959" />



## Result
Thus Execution of Network commands Performed 
