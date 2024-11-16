# 2c.SIMULATING ARP /RARP PROTOCOLS
## NAME : VEERARAGAVAN V
## REGISTER NUMBER : 212223230237
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
## PROGRAM - ARP
### CLIENT
```py
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"SA:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode()) 
    except KeyError:
        c.send("Not Found".encode())

```
### SERVER
```py
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 ip=input("Enter logical Address: ")
 s.send(ip.encode())
 print("MAC Address",s.recv(1024).decode())

```
## OUPUT - ARP
### CLIENT OUTPUT
![CLIENT1 (1)](https://github.com/user-attachments/assets/d9207dfc-f06e-45a5-97d2-8b7fc11a3bd0)

### SERVER OUTPUT
![SERVER1 (1)](https://github.com/user-attachments/assets/abd1ea31-b1a4-4003-886b-d0879e1ad07d)

## PROGRAM - RARP
### CLIENT
```py
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
 ip=c.recv(1024).decode()
 try:
     c.send(address[ip].encode())
 except KeyError:
     c.send("Not Found".encode())

```
### SERVER
```py
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
### CLIENT OUTPUT
![CLIENT1](https://github.com/user-attachments/assets/271ff84d-50d0-43a1-8bf6-366011ff134d)

### SERVER OUTPUT
![SERVER1](https://github.com/user-attachments/assets/9bd7f54d-faed-4d86-92b2-0ac355da9cd6)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
