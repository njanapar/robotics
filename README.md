# Simple Browser Application Using `socket.io`

## 1. OVERVIEW

This project demonstrates a simple browser-based application that facilitates secure communication between Python and JavaScript using `socket.io`. Key features include:

- Secure server setup (`https` vs `http`)
- Accessibility via `https://localhost:8080` (or `https://<your-ip>:8080`)
- Real-time message/data exchange between Python and JavaScript

---

## 3. HOW TO RUN THE SYSTEM

### Step 1: Open Two Terminal Windows
Navigate to the `simple_browser_socket` directory in both terminals.

### Step 2: Start the Secure Server
Run the following command in the first terminal:

```bash
node server_secure.cjs --public
```
### Step 3: Launch the Python Client
Run the following command in the second terminal:

```bash
python3 client.py
```
## 4. UNDERSTANDING THE CONCEPT BEHIND THE SIMPLE BROWSER SOCKET

### What is socket.io?
`socket.io` is a library that enables real-time, bidirectional, and event-based communication between clients and servers.

### How Does This Project Work?
1. The **server** (Node.js) acts as a WebSocket server, allowing real-time communication over HTTPS.
2. The **client** (Python script) connects to the WebSocket server and exchanges messages.
3. The **browser** (`index.html`) is the front-end, which sends and receives messages from the server.
4. The data flow happens through events, where:
   - The server **publishes topics** (messages).
   - The client **subscribes to topics** and responds accordingly.
## Roles of Different Files

- **server_secure.cjs**: Handles WebSocket communication and routes messages.
- **client.py**: Connects to the WebSocket and sends/receives data.
- **index.html**: Displays the interface and communicates with the server.
