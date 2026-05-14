# Secure Chatroom-Based P2P File Transfer System

A secure hybrid client-server and peer-to-peer (P2P) communication system built in C using TCP sockets, OpenSSL, and POSIX threads on Linux.

The project combines centralized chatroom coordination with direct encrypted peer-to-peer messaging and file transfer to reduce server load, improve scalability, and enhance privacy.

---

## Key Concepts

- TCP Socket Programming
- Peer-to-Peer (P2P) Networking
- Client-Server Architecture
- RSA & AES Encryption
- POSIX Threads (pthreads)
- Linux System Programming
- OpenSSL Integration
- Concurrent Programming
- Secure File Transfer

---

## Why This Project?

Traditional centralized messaging systems route all messages and files through a server, increasing bandwidth usage, latency, and infrastructure overhead.

This project explores a hybrid architecture where:
- the server handles coordination and security bootstrap
- clients communicate directly for actual data transfer

This improves bandwidth efficiency, scalability, and privacy while demonstrating low-level systems and networking concepts.

---

## Features

- Secure client-server communication
- Peer-to-peer (P2P) direct messaging
- Encrypted file transfer using AES
- RSA-based secure key exchange
- Chatroom creation and management
- Multi-client support using pthreads
- Linux socket programming
- Command-line interface (CLI)

---

## Architecture

The system follows a hybrid architecture:

### Central Server Responsibilities
- Client registration
- Chatroom creation and membership management
- Peer discovery
- RSA-based AES key distribution

### Peer-to-Peer Responsibilities
- Direct client-to-client messaging
- Direct encrypted file transfer
- Reduced server bandwidth and latency

---

## Technologies Used

- C Programming Language
- TCP Socket Programming
- POSIX Threads (pthreads)
- OpenSSL
  - RSA Encryption
  - AES-CFB Encryption
- Linux / WSL
- GCC

---

## Project Structure

```bash
.
├── include/
│   └── common.h
│
├── src/
│   ├── main.c
│   ├── server.c
│   ├── client.c
│   ├── p2p.c
│   └── encryption.c
│
├── Makefile
└── README.md
```

---

## Security Design

### RSA Encryption
Used for:
- Secure AES key exchange

Each client:
- Generates RSA public/private key pair
- Sends public key to server

Server:
- Encrypts AES key and IV using client public key

### AES Encryption
Used for:
- Message encryption
- File encryption

Mode:
- AES-CFB

---

## Communication Flow

### Client ↔ Server
Used for:
- Authentication
- Chatroom management
- Peer discovery
- Secure key exchange

### Client ↔ Client (P2P)
Used for:
- Direct message transfer
- Direct file transfer

---

## Build Instructions

### Prerequisites

Install required packages:

```bash
sudo apt update
sudo apt install build-essential libssl-dev
```

### Compile

```bash
make
```

---

## Running the Application

### Start Server

```bash
./chat_app server
```

### Start Client

Open multiple terminals and run:

```bash
./chat_app client
```

---

## Supported Commands

### Chatroom Commands

```bash
/createroom <room_name>
/listrooms
/joinroom <room_id>
/leaveroom <room_id>
/listmembers <room_id>
```

### Messaging Commands

```bash
/msg <client_number> <message>
/broadcast <message>
```

### File Transfer

```bash
/sendfilegroup <filename>
```

---

## Example Workflow

1. Start server
2. Connect multiple clients
3. Create and join chatrooms
4. Send encrypted messages
5. Transfer files directly between peers

---

## Current Limitations

- Fixed maximum client count
- Local/LAN deployment focused
- No NAT traversal support
- No offline message storage
- Blocking socket implementation
- Global AES key/IV shared across clients

---

## Future Improvements

- GUI frontend
- NAT traversal (STUN/TURN)
- Dynamic scaling
- Authenticated encryption (AES-GCM)
- Non-blocking sockets with epoll
- Persistent offline messaging

---

## What I Learned

- Building concurrent networked systems in C
- Implementing TCP socket communication
- Integrating OpenSSL for secure communication
- Designing hybrid client-server + P2P architectures
- Managing multithreaded communication flows
- Understanding real-world tradeoffs between scalability, security, and simplicity

---

## Platform

Tested on:
- Ubuntu Linux
- WSL (Windows Subsystem for Linux)

---

## Clean Build Files

```bash
make clean
```
