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
Server.py
```
import socket
# Create socket
server = socket.socket()
# Bind IP and port
server.bind(("127.0.0.1", 5555))
# Listen for client
server.listen(1)
print("Server waiting for connection...")
# Accept client
client, addr = server.accept()
print("Connected to:", addr)
# Ask filename
filename = input("Enter file name to send: ")
# Open and send file
with open(filename, "rb") as file:
 data = file.read()
 client.send(data)
print("File sent successfully")
# Close connections
client.close()
server.close()

```

Client.py
```
import socket
# Create socket
client = socket.socket()
# Connect to server
client.connect(("127.0.0.1", 5555))
# Save file name
save_name = input("Enter name to save file: ")
# Receive data
data = client.recv(1000000)
# Save file
with open(save_name, "wb") as file:
 file.write(data)
print("File received successfully")
# Close connection
client.close()
```

## OUPUT
Server.py:

<img width="402" height="173" alt="image" src="https://github.com/user-attachments/assets/ce277ce4-7a11-4fcb-9b65-30e8eb8c3fc6" />

Client.py:

<img width="395" height="152" alt="image" src="https://github.com/user-attachments/assets/cc181552-ec1c-44e2-9cd0-6e9a81d0ead5" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
