# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
```
server.py
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("ARP Server Started...")
c, addr = s.accept()
print("Connected with:", addr)

# IP Address and MAC Address table
address = {
    "165.165.80.80": "6A:08:AA:C2",
    "165.165.79.1": "8A:BC:E3:FA",
    "192.168.1.1": "AA:BB:CC:DD"
}

while True:
    ip = c.recv(1024).decode()

    if not ip:
        break

    print("Requested IP Address:", ip)

    if ip in address:
        mac = address[ip]
        reply = "MAC Address for " + ip + " is " + mac
    else:
        reply = "IP Address Not Found"

    c.send(reply.encode())

c.close()
s.close()

client.py
import socket

s = socket.socket()
s.connect(('localhost', 8000))

print("Connected to ARP Server")

while True:
    ip = input("Enter IP Address : ")

    if ip.lower() == "exit":
        break

    s.send(ip.encode())

    result = s.recv(1024).decode()
    print(result)

s.close()
```
## OUPUT - ARP
SERVER
<img width="1420" height="229" alt="image" src="https://github.com/user-attachments/assets/39727d74-94f7-470c-8a19-ac5f41accc79" />

CLIENT
<img width="1420" height="229" alt="image" src="https://github.com/user-attachments/assets/74f997e6-f3f0-409e-a0a8-3471d85c7bbe" />


## PROGRAM - RARP
## OUPUT -RARP
## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
