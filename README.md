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
SERVER
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
ip=c.recv(1024).decode()
try:
c.send(address[ip].encode())
except KeyError:
c.send("Not Found".encode())
```

CLIENT:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
ip=input("Enter logical Address : ")
s.send(ip.encode())
print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP

<img width="957" height="1072" alt="image" src="https://github.com/user-attachments/assets/b9a363e1-6352-4e77-97b8-7453a34cfbe5" />
<img width="944" height="1019" alt="image" src="https://github.com/user-attachments/assets/e54183ef-8da3-48ca-beba-bea70b75c445" />

## PROGRAM - RARP
SERVER;
```
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
CLIENT:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
ip=input("Enter MAC Address : ")
s.send(ip.encode())
print("Logical Address",s.recv(1024).decode())

```
## OUPUT -RARP
<img width="951" height="1046" alt="image" src="https://github.com/user-attachments/assets/31259f13-aea1-40b6-b043-2fc92470023e" />

<img width="952" height="1041" alt="Screenshot 2026-05-13 105124" src="https://github.com/user-attachments/assets/287efa7d-cfbb-4f8d-bbb3-0d79ed7aff12" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
