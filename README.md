# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM
SERVER.PY
```
import socket

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

server_socket.bind(("localhost", 5000))

server_socket.listen(1)

print("Server waiting for connection...")

conn, addr = server_socket.accept()
print("Connected to:", addr)

while True:
    message = conn.recv(1024).decode()
    print("Client:", message)

    if message.lower() == "exit":
        break

    reply = input("Server: ")
    conn.send(reply.encode())

    if reply.lower() == "exit":
        break

conn.close()
server_socket.close()
```
CLIENT.PY
```
import socket

client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

client_socket.connect(("localhost", 5000))

print("Connected to server.")

while True:
    message = input("Client: ")
    client_socket.send(message.encode())

    if message.lower() == "exit":
        break

    reply = client_socket.recv(1024).decode()
    print("Server:", reply)

    if reply.lower() == "exit":
        break

client_socket.close()
```
## OUPUT
SERVER.PY

<img width="440" height="259" alt="image" src="https://github.com/user-attachments/assets/b3e3bfca-22c6-420b-a807-fb1fb76893dc" />

CLIENT.PY

<img width="433" height="278" alt="image" src="https://github.com/user-attachments/assets/65f935e3-6732-4cd0-839a-0579ff519c40" />

## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
