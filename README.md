4.Execution_of_NetworkCommands
AIM :Use of Network commands in Real Time environment
Software : Command Prompt And Network Protocol Analyzer
Procedure: To do this EXPERIMENT- follows these steps:

In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer
All commands related to Network configuration which includes how to switch to privilege mode
and normal mode and how to configure router interface and how to save this configuration to
flash memory or permanent memory.
This commands includes
• Configuring the Router commands
• General Commands to configure network
• Privileged Mode commands of a router
• Router Processes & Statistics
• IP Commands
• Other IP Commands e.g. show ip route etc.
Program
##server
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
##client
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
##server
<img width="838" height="522" alt="image" src="https://github.com/user-attachments/assets/4bd212b8-fa77-447b-b7dc-0c1ae70e4549" />
##client
<img width="797" height="296" alt="image" src="https://github.com/user-attachments/assets/df167e8c-2111-4015-9218-c562799ba3a5" />



## Result
Thus Execution of Network commands Performed 
