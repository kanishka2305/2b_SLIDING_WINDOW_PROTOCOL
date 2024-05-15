# EXP: 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM:
To implement to sliding window protocol.
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM:
### Client:
```py
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
 while(i<len(l)):
 st+=s
 c.send(str(l[i:st]).encode())
 ack=c.recv(1024).decode()
 if ack:
 print(ack)
 i+=s
```
### Server:
```py
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True: 
 print(s.recv(1024).decode())
 s.send("acknowledgement recived from the server".encode())
```
## OUPUT:
### Client:
![323607020-d7e60a2b-08e5-41a0-8a35-d7eedc47a426](https://github.com/kanishka2305/2b_SLIDING_WINDOW_PROTOCOL/assets/113497357/dd6e5dc5-6df2-4529-9674-562d842421a9)

### Server:
![323607128-b7363e32-7a76-4f13-9354-5d19aac1dcaf](https://github.com/kanishka2305/2b_SLIDING_WINDOW_PROTOCOL/assets/113497357/fbcaccac-fb58-47a3-af8a-61338d429aa2)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
