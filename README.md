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
```
NAME: SHARMA R
REG.NO: 212224230261
```
## PROGRAM - ARP
## CLIENT
```
import socket
s = socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c, addr = s.accept()
address = {"10.34.8.47":"168:34:21:98:2D:AD"}
while True:
    ip = c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())

```
## SERVER
```
import socket
s = socket.socket()
s.connect(('localhost',8000))
while True:
    ip = input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address:", s.recv(1024).decode())
```
## OUPUT - ARP
<img width="1281" height="286" alt="arp" src="https://github.com/user-attachments/assets/d8682899-51f2-48ba-825d-b76818bfc6c9" />

## PROGRAM - RARP
## CLIENT
```
import socket
s = socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c, addr = s.accept()
address = {"168:34:21:98:2D:AD":"10.34.8.47"}
while True:
    ip = c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
## SERVER
```
import socket
s = socket.socket()
s.connect(('localhost',9000))
while True:
    ip = input("Enter MAC Address : ")
    s.send(ip.encode())
    print("logical Address:", s.recv(1024).decode())
```
## OUPUT -RARP
<img width="1548" height="110" alt="arap" src="https://github.com/user-attachments/assets/95d9f9b1-4339-433d-b790-aa78b3e29f82" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
