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
## PROGRAM - ARP :
## Client
~~~
Client

socket 
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
~~~

## Server:

~~~
Server

import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True: 
     ip=input("Enter logical Address : ") 
     s.send(ip.encode()) 
     print("MAC Address",s.recv(1024).decode())
~~~

## OUTPUT - ARP:
<img width="1153" height="392" alt="image" src="https://github.com/user-attachments/assets/1973b58a-3fd6-4260-901f-fffd6c899e56" />
<img width="1280" height="251" alt="image" src="https://github.com/user-attachments/assets/eaf01de1-dcdc-4e66-bda4-2e4660972abe" />


## PROGRAM-RARP:
## Client
~~~
Client

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
~~~

## Server:

~~~
Server

import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
~~~

## OUTPUT-RARP:
<img width="1136" height="405" alt="image" src="https://github.com/user-attachments/assets/2d17a696-fd86-4cbd-b9df-51c683295e6d" />
<img width="1280" height="253" alt="image" src="https://github.com/user-attachments/assets/52d63eb2-88ec-4a2a-9e85-2b70e1802f52" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
