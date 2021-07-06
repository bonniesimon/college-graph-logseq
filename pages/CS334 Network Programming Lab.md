- [GeekForGeeks : using all three methods](https://www.geeksforgeeks.org/multiprocessing-python-set-2/)
- [IPC using pipes](https://prgwonders.blogspot.com/2016/08/write-ipc-program-using-pipe-using-c.html)
- [Using shared memory in python](https://docs.python.org/3/library/multiprocessing.shared_memory.html) But I didn't fully understand this
- [[NW Lab Exp 3]]
- [[NW Lab Exp 8]]
- socket working
-
  ```python
  python
  s = socket.socket(address_family, connection_type)
  # address_family - AF_INET (ipv4)
  # connection type - socket.SOCK_STREAM (TCP), socket.SOCK_DGRAM(UDP)
  
  # specifying the host and port
  s.bind((host, port))
  
  # Server-------------------------------
  # listening to specified port in bind. Not sure what 5 is.
  # The listen() function accepts a queue size through the parameter backlog. 
  # This denotes maximum number of connections 
  # that can be queued for this socket by the operating system. 
  # Once 'backlog' number of connections is in the socket's queue,
  # the kernel will reject incoming connections to the socket.
  serversocket.listen(5)
  
  # .accept method return a tuple (socketForClient and addr)
  clientsocket, addr = serversocket.accept()
  
  # to send to client; clientsocket from prev line
  clientsocket.send(msg_byte)
  # to close connection
  clientsocket.close()
  
  # Client--------------------------------
  # to connect to the server listening at host, port
  clientsocket.connect((host, port))
  
  # To receive as bytes from server; max receive capacity is 1024 byte
  msg_byte = clientsocket.recv(1024)
  
  # to close connection
  clientsocket.close()
  ```
-