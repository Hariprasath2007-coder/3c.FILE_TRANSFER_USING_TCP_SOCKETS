# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## Name : HARI PRASATH E
## Ref No : 25007799
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
## Server site
```
import socket

s = socket.socket()

host = socket.gethostname()
port = 60000

s.bind((host, port))

s.listen(1)

print("Server listening...")

c, addr = s.accept()

print("Connected with", addr)

msg = c.recv(1024).decode()

print("Client says:", msg)

filename = "sample.txt"

file = open(filename, "rb")

data = file.read(1024)

while data:
    c.send(data)
    data = file.read(1024)

print("File sent successfully")

file.close()
c.close()
s.close()

```
## Client Site

```
import socket

s = socket.socket()

host = socket.gethostname()
port = 60000

s.connect((host, port))

s.send("Hello Server".encode())

file = open("received_file.txt", "wb")

print("Receiving file...")

while True:
    data = s.recv(1024)

    if not data:
        break

    file.write(data)

print("File received successfully")

file.close()
s.close()

```
## Sample.txt file
```
Computer Networks enable communication between computers and devices.

There are different types of networks such as:
1. LAN (Local Area Network)
2. MAN (Metropolitan Area Network)
3. WAN (Wide Area Network)

TCP/IP protocol is used for reliable communication.

Sockets are used in Python to create client-server applications.

File transfer using TCP sockets allows one computer to send data files to another computer through a network.
```
## OUPUT
<img width="1916" height="1079" alt="image" src="https://github.com/user-attachments/assets/2c0b93bf-ed0c-41d9-b622-b59ea061263a" />
<img width="1909" height="1079" alt="image" src="https://github.com/user-attachments/assets/717f24d0-9d8d-4614-ad8a-70094d31e95f" />
<img width="1917" height="1079" alt="image" src="https://github.com/user-attachments/assets/ba9f0c90-16ce-4870-8012-53b1922a6d5f" />


## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
