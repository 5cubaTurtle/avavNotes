import: `import socket`

### functions
get current [[hostname]]: `hostname = socket.gethostname()`

### setup tcp connection
TCP server:
```python
import socket

# create a TCP socket
sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# bind the socket to a specific IP address and port
sock.bind(('127.0.0.1', 12345))

# listen for incoming connections
sock.listen(1)

# wait for a client to connect
print('Waiting for a connection...')
client_sock, client_addr = sock.accept()
print('Connection established:', client_addr)

# receive data from the client
data = client_sock.recv(1024)
print('Received data:', data.decode())

# send a response to the client
response = 'Hello from the server!'
client_sock.sendall(response.encode())

# close the connection
client_sock.close()
sock.close()
```

TCP client:
```python
import socket

# create a TCP socket
sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# connect to the server
sock.connect(('127.0.0.1', 12345))

# send data to the server
message = 'Hello from the client!'
sock.sendall(message.encode())

# receive a response from the server
response = sock.recv(1024)
print('Received response:', response.decode())

# close the connection
sock.close()
```
In the server code, we first create a TCP socket and bind it to a specific IP address and port. We then listen

### setup UDP connection
UDP Server:
```python
import socket

UDP_IP = "127.0.0.1"
UDP_PORT = 5005

sock = socket.socket(socket.AF_INET,  # Internet
                     socket.SOCK_DGRAM)  # UDP
sock.bind((UDP_IP, UDP_PORT))

while True:
    data, addr = sock.recvfrom(1024)  # buffer size is 1024 bytes
    print("received message:", data)
```

UDP Client:
```python
import socket

UDP_IP = "127.0.0.1"
UDP_PORT = 5005
MESSAGE = b"Hello, World!"

sock = socket.socket(socket.AF_INET,  # Internet
                     socket.SOCK_DGRAM)  # UDP
sock.sendto(MESSAGE, (UDP_IP, UDP_PORT))
```
Note that in this example, the server is listening on the local loopback address (`127.0.0.1`) and port `5005`, while the client is sending a message to that same address and port. You can adjust these values to match your specific use case.

