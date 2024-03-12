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
```
Server

import socket

def send_file(client_socket, file_path):
    with open(file_path, 'rb') as file:
        data = file.read(1024)
        while data:
            client_socket.send(data)
            data = file.read(1024)

def main():
    host = '127.0.0.1'
    port = 12345

    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server_socket.bind((host, port))
    server_socket.listen(1)

    print(f"Server listening on {host}:{port}")

    client_socket, client_addr = server_socket.accept()
    print(f"Connection from {client_addr}")

    file_path = 'example.txt'

    send_file(client_socket, file_path)

    client_socket.close()
    server_socket.close()

if __name__ == "__main__":
    main()
```
```
Client

import socket

def receive_file(server_socket, file_path):
    with open(file_path, 'wb') as file:
        data = server_socket.recv(1024)
        while data:
            file.write(data)
            data = server_socket.recv(1024)

def main():
    host = '127.0.0.1'
    port = 12345

    client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    client_socket.connect((host, port))

    print(f"Connected to {host}:{port}")

    file_path = 'received_file.txt'

    receive_file(client_socket, file_path)

    client_socket.close()

if __name__ == "__main__":
    main()
```
## OUPUT

## Server
![Screenshot 2024-03-12 184426](https://github.com/Srikaavyaathamizh/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/144870938/bc664a1d-8bde-46dc-926a-fa52629bf14c)

## Client
![Screenshot 2024-03-12 184440](https://github.com/Srikaavyaathamizh/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/144870938/7f45b4db-d19c-42eb-8805-da25048bd680)


## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
