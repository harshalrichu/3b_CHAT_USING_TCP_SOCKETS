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
client.py
```
import socket
s=socket.socket()
s.connect(('localhost', 8000))
print("Connected to server")
while True:
    msg = input("Client > ")
    s.send(msg.encode())
    if msg.lower() == "exit":
        print("Disconnected from server")
        break
    serverReply = s.recv(1024).decode()    
    if serverReply.lower() == "exit":
        print("Server closed connection")
        break 
    print("Server >", serverReply)
s.close()
```
server.py
```
import socket
s=socket.socket()
s.bind(('localhost', 8000))
s.listen(1)
print("Waiting for connection...")
c, addr=s.accept()
print("Connected to", addr)
while True:
    clientMessage = c.recv(1024).decode()  
    if clientMessage.lower() == "exit":
        print("Client disconnected")
        break
    print("Client >", clientMessage)
    msg = input("Server > ")
    c.send(msg.encode())
    if msg.lower() == "exit":
        print("Server stopped")
        break
c.close()
s.close()
```
## OUPUT
<img width="1021" height="237" alt="Screenshot 2026-03-10 090453" src="https://github.com/user-attachments/assets/660b3689-700a-4fe7-a3c6-dbe6db758f2c" />
<img width="1018" height="235" alt="Screenshot 2026-03-10 090500" src="https://github.com/user-attachments/assets/57a7df58-7e0f-4dff-9caf-9ce9f9f22c8c" />

## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
