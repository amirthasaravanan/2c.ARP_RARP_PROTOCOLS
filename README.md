# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP and RARP protocol using UDP.
## ALGORITHM FOR ARP:
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
# Client:
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
# Server:
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
# Client:
![clientarp](https://github.com/user-attachments/assets/2f7205ec-7107-45e8-810b-444ee17c6dc0)

# Server:
![serverarp](https://github.com/user-attachments/assets/ac429761-cb04-4da0-8724-8d22e23c9d56)
## ALGORITHM FOR RARP:
## Client:
1. Start the program 
2. Using datagram sockets UDP function is established. 
3. Get the MAC address to be converted into IP address. 
4. Send this MAC address to server. 
5. Server returns the IP address to client.
## Server:
1. Start the program. 
2. Server maintains the table in which IP and corresponding MAC addresses are stored. 
3. Read the MAC address which is send by the client. 
4. Map the IP address with its MAC address and return the IP address to client.
   

## PROGRAM - RARP
# Client:
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
# Server:
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
# Client:
![clientRARP](https://github.com/user-attachments/assets/feb9f531-5484-4b5f-8a42-b39fe69629ef)
# Server:
![serverRARP](https://github.com/user-attachments/assets/80b39deb-915e-4827-9edd-dd926575de63)



## RESULT
Thus, the python program for simulating ARP protocols using TCP and RARP protocol using UDP was successfully 
executed.
