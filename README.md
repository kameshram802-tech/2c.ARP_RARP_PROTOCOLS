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
### SERVER.py
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode()) 
```
### CLIENT.py
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA","169.254.110.248":"FC:6D:77:6F:D2:A9"};
while True:
    ip=c.recv(1024).decode()
    try:
       c.send(address[ip].encode())
    except KeyError:
       c.send("Not Found".encode())
```
## OUPUT - ARP
## SERVER
<img width="953" height="387" alt="Screenshot 2026-05-12 141441" src="https://github.com/user-attachments/assets/985e76e3-35f2-49eb-b3ce-a2f5cad2161d" />

## CLIENT
<img width="965" height="396" alt="Screenshot 2026-05-12 141425" src="https://github.com/user-attachments/assets/73861dbe-18ca-47a9-b019-d42f065f2c41" />

## PROGRAM - RARP
### SERVER.py
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())

```
### CLIENT.py
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"165.165.80.80","FC:6D:77:6F:D2:A9":"169.254.110.248"};
while True:
    ip=c.recv(1024).decode()
    try:
       c.send(address[ip].encode())
    except KeyError:
       c.send("Not Found".encode())
```
## OUPUT -RARP
## SERVER
<img width="958" height="410" alt="Screenshot 2026-05-12 141746" src="https://github.com/user-attachments/assets/5b0c94da-362d-4e88-bb24-3bc9a9202d2d" />

## CLIENT
<img width="957" height="409" alt="Screenshot 2026-05-12 141735" src="https://github.com/user-attachments/assets/731c09f0-f278-4acb-a6cc-438e145301c5" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
