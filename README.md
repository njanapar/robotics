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
