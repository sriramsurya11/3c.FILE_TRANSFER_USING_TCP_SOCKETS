# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
### client:
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
### server:
```
import socket                    
port = 60000                    
s = socket.socket()              
host = socket.gethostname()      
s.bind((host, port))
s.listen(5)                      
while True:
   conn, addr = s.accept()      
   data = conn.recv(1024) 
   print('Server received', repr(data)) 
   filename='mytext.txt' 
   f = open(filename,'rb') 
   l = f.read(1024) 
   while (l): 
      conn.send(l) 
      print('Sent ',repr(l)) 
      l = f.read(1024) 
   f.close() 
   print('Done sending') 
   conn.send('Thank you for connecting'.encode()) 
   conn.close() 
```
## OUPUT
### client:
![315955065-cb8a84c0-6789-4a69-97f4-3b949d228c3d](https://github.com/sriramsurya11/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/151637759/6bc3eb70-ff1f-4dc2-90d0-a34ffe95902f)

### server
![315955101-744fc4f7-0ba6-45ec-b480-44749843866e](https://github.com/sriramsurya11/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/151637759/196553be-acdd-4313-8e20-55d763907b13)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
