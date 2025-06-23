Think of a **wall socket** (power outlet):
- You **plug in** a device (like a phone charger)
- Power flows through
- You don’t care about how wires are arranged inside the wall

**socket API only gives your app the actual data payload** (like an HTTP request body), not the raw packet contents..

A large HTTP response is sent by a server, and it gets broken into 3 TCP packets on the way.
- NIC receives 3 raw Ethernet frames.
- OS strips Ethernet, IP, and TCP headers.
- OS **reorders** them if needed using TCP sequence numbers.
- OS **reassembles** the original stream of bytes.
- OS **buffers the data in the socket buffer** (kernel space).
- App calls `recv()` → **gets data from the buffer**.

The **socket only exposes the reassembled stream**, not partial packets.

- In the OS (kernel), **each open socket has its own receive buffer and send buffer**.
- These are internal memory areas allocated and managed by the **TCP/IP stack**.
- So we don’t say “general OS buffer” — we say **socket buffer** because it belongs to that particular socket instance.
- When data arrives over the network, the OS stores it in the **receive buffer** of the socket.
- When your app sends data, it goes into the **send buffer** of the socket.
**each app (or connection) must have its own socket**, which is internally mapped to this tuple to ensure uniqueness.

A TCP connection is uniquely identified by the following
<Protocol, Source IP, Source Port, Destination IP, Destination Port>
- **Source Port (ephemeral)** is chosen by client OS dynamically (e.g., 34567)
- **Destination Port** is usually fixed (e.g., 80 for HTTP)
When a client connects, the server:
- Accepts the connection
- Creates a **new socket** with the client’s 5-tuple
- Keeps listening on the original socket for new clients
- 
eg
- The TCP/IP stack **bakes the cake** (handles order, retries, etc.)
- The socket buffer is **the cake tray**, holding the ready-to-serve cake
- Your app uses the **socket API to eat the cake slice-by-slice**