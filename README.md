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
## Code Explanation
# Main Class Explanation

## `__init__`:
- Initializes the graceful shutdown mechanism by creating an instance of `GracefulShutdown`.
- Subscribes to Socket.IO events (`chat`, `direction`) to listen for messages from the server. It then defines what to do when these events are received.
- Connects to the Socket.IO server using `sio.connect()` with the server address `'https://localhost:8080'` (can be changed to other IPs).
- After the connection is established, it enters a loop that runs until the program is shut down, checking every 1/5 Hz (every 5 seconds) to keep the loop running smoothly.

## Socket.IO Events:
- **`@sio.on('chat')`**: 
  - Listens for `chat` messages from the server. When a message is received, the `callback_chat` function is called, which prints the received message and sends a reply back to the server.
  
- **`@sio.on('direction')`**: 
  - Listens for `direction` messages. When a direction message (like "up", "down", etc.) is received, it prints the direction and sends a response (`reply`).

## Helper Functions in Main:
- **`callback_chat(self, data)`**: 
  - Handles incoming chat messages. It simply prints the data and replies with the same message back to the server.

- **`doSomething(self)`**: 
  - A placeholder function for doing anything continuously while the program runs. Currently, it doesn't perform any action.

- **`pubNotice(self, txt)`**: 
  - Sends a notice to the server under the `notices` topic. This could be used for logging or status updates.

- **`shutdown(self)`**: 
  - Handles the shutdown procedure by disconnecting from the server and cleaning up any resources.

## Main Execution Block:
- **`if __name__ == "__main__"`**: 
  - Ensures that when this script is run, an instance of the `Main` class is created, which starts the connection to the server, handles events, and runs the loop.

