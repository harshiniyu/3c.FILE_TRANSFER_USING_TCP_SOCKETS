# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM:
## CLIENT:
```import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
print("Server listening on port", port)
while True:
    conn, addr = s.accept()
    print("Connected to", addr)
    data = conn.recv(1024)
    print('Server received', repr(data))
    filename = 'C:/Users/admin/Desktop/cn/Harshini.txt'
    with open(filename, 'rb') as f:
        chunk = f.read(1024)
        while chunk:
            conn.send(chunk)
            print('Sent', repr(chunk))
            chunk = f.read(1024)

    print('Done sending')
    conn.send("Thank you for connecting".encode())
    conn.close()
```
## SERVER:
```import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file.txt', 'wb') as f:
    print('Receiving data...')
    while True:
        data = s.recv(1024)
        if not data:
            break
        f.write(data)
print('Successfully received the file')
s.close()
print('Connection closed')
```
## OUPUT:
![Screenshot 2024-10-10 104050](https://github.com/user-attachments/assets/a623f1c8-4856-4fa5-86e3-774589023a7e)
![Screenshot 2024-10-10 104100](https://github.com/user-attachments/assets/c1588126-05a7-4909-8974-c9b51169bd27)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
