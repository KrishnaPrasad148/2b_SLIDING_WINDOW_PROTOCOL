# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM

#### Client side:
```
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

#### Sevrer side:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())
```
## OUPUT

![Screenshot 2024-04-20 134817](https://github.com/KrishnaPrasad148/2b_SLIDING_WINDOW_PROTOCOL/assets/147332763/f212f658-2ed7-440a-9296-5f5cc1d143d3)


![Screenshot 2024-04-20 134828](https://github.com/KrishnaPrasad148/2b_SLIDING_WINDOW_PROTOCOL/assets/147332763/975c5a5d-5ea1-43d5-95e7-e2c88b0b0c90)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
