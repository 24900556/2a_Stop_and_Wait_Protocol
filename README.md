# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
### SERVER
```
import socket

s = socket.socket()
s.bind(('localhost', 8001))   
s.listen(5)
c, addr = s.accept()
print("Connected with", addr)

while True:
    i = input("Enter data: ")
    c.send(i.encode())
    ack = c.recv(1024).decode()
    if ack:
        print("Server received:", ack)
    else:
        c.close()
        break
```
### CLIENT
```
import socket

s = socket.socket()
s.connect(('localhost', 8001))   
while True:
    data = s.recv(1024).decode()
    if not data:
        break
    print("Client received:", data)
    s.send("Acknowledgement Received".encode())

```
## OUTPUT
<img width="1920" height="1140" alt="image" src="https://github.com/user-attachments/assets/7b06152d-71f1-4d48-849e-2a54f6bec229" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
