# EX.NO:3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS

## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
# client.py
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
    while True:
        print('receiving data...')
        data = s.recv(1024)
        print('data=%s', (data))
        if not data:
            break
        f.write(data)
f.close()
print('Successfully get the file')
s.close()
print('connection closed')
```

# server.py
```
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
while True:
    conn, addr = s.accept()
    data =conn.recv(1024)
    print('Server received', repr(data))
    filename='mytext.txt'
    f = open(filename,'rb')
    l = f.read(1024)
    while (l):
        conn.send(l)
        print('Sent',repr(l))
        l =f.read(1024)
    f.close()
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.clo
se()
```

## OUPUT
# client.py
<img width="408" height="148" alt="image" src="https://github.com/user-attachments/assets/804ca98f-50fa-4ca5-881b-7397f4e897c0" />

# server.py
<img width="446" height="68" alt="image" src="https://github.com/user-attachments/assets/d8bd43b5-1d86-4157-8f72-c602e8a5658a" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was successfully created and executed.
