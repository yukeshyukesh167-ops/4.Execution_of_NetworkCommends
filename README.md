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

## Program 
# server
```
import socket
import subprocess
import platform
server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
host = "127.0.0.1"
port = 6000
server.bind((host, port))
server.listen(1)
print("Server started... Waiting for connection...")
conn, addr = server.accept()
print("Connected to:", addr)
while True:
    command = conn.recv(1024).decode()
    if command.lower() == "exit":
        print("Client disconnected.")
        break
    print("Command received:", command)
    try:
        output = subprocess.check_output(command, shell=True)
        conn.send(output)
    except Exception as e:
        conn.send(str(e).encode())
conn.close()
server.close()
```
# client 
```
import socket
client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
host = "127.0.0.1"
port = 6000
client.connect((host, port))
print("Connected to Server")
print("You can use commands like: ping google.com, ipconfig, netstat, nslookup google.com")
print("Type 'exit' to quit")
while True:
    command = input("\nEnter Network Command: ")
    client.send(command.encode())
    if command.lower() == "exit":
        break
    output = client.recv(4096).decode()
    print("\n--- Command Output ---")
    print(output)
client.close()
```

## Output
### CLIENT:
<img width="889" height="555" alt="image" src="https://github.com/user-attachments/assets/1689874c-57e9-44d6-8bd9-67aefa389ddd" />

### SERVER:
<img width="798" height="290" alt="image" src="https://github.com/user-attachments/assets/dd2d2811-b22d-4d89-ac97-32f0f3c415c8" />

## Result
Thus Execution of Network commands Performed 
