network interface driver
- Handles sending/receiving raw packets to/from hardware (e.g., your Wi-Fi or Ethernet card).

socket layer
- Interface exposed to user programs (your app uses sockets to send/receive data).

### **Typical flow inside OS**

- Your app calls a **socket API** like `send()` to send data ( http request) .
- Data goes to the **socket buffer** in kernel memory.
- TCP breaks data into segments, adds TCP headers, passes packets to IP layer.
- IP layer adds IP headers, sends packets to network driver.
- Network driver transmits bytes over physical medium.
    
On the **receiving side**:
- Network driver receives packets.
- IP layer verifies destination IP, sends packet to TCP layer.
- TCP layer checks sequence numbers, acknowledges, reassembles data.
- Data passed up to socket buffer.
- Your app reads data via `recv()`.

# Connection

tcp handshake connection happens in 3 step

![[Pasted image 20250529130603.png|600]]

tcp connection termination

![[Pasted image 20250529130635.png|600]]


OS manages the tcp part for both server and client perspective . 

system call from client perspective 

```python
socket()     # Create a TCP socket
connect()    # Ask OS to connect to server (initiates TCP handshake)
send()       # Pass data to OS
recv()       # Ask OS for response data
close()      # Ask OS to close connection
```

system call from server perspective

```python
socket()      # Create a TCP socket
bind()        # Bind to a port (e.g., 80 or 443)
listen()      # Listen for incoming connections
accept()      # Accept a new connection (creates a new socket)
recv()/send() # Handle request/response
close()       # Close client connection
```

handshake 
- **Client OS sends SYN** packet
- **Server OS replies SYN-ACK**
- **Client OS sends ACK**

	