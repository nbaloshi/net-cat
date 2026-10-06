# Net-Cat

A command-line TCP chat server written in Go, inspired by the Netcat (`nc`) utility.

The server accepts multiple client connections and provides a real-time group chat where connected users can communicate through a central TCP server.

## Features

* TCP server using Go's `net` package
* Multiple simultaneous clients
* Real-time group messaging
* Concurrent client handling with goroutines
* Client connection management
* Maximum client limit
* Username management
* `/name` command for changing usernames
* Connection and server error handling
* Command-line server configuration

## Tech Stack

* Go
* TCP/IP networking
* Go `net` package
* Goroutines
* Mutex-based concurrency control
* Command-line interface

## Project Structure

```text
.
├── handlers
│   ├── Broadcast.go
│   ├── HandleConnection.go
│   ├── LocalIP.go
│   ├── Port.go
│   ├── PreviousMessages.go
│   ├── ValidateUser.go
│   └── WelcomeMessage.go
│
├── server
│   └── TCPChat.go
│
├── .gitignore
├── go.mod
└── README.md
```

## How It Works

The server listens for TCP connections on a specified port.

When a client connects:

1. The server accepts the TCP connection.
2. The client is checked against the maximum client limit.
3. A goroutine handles the client connection.
4. Messages can be broadcast to other connected clients.
5. Connected users can manage their username through chat commands.

The project uses synchronization around shared client state to safely manage multiple connections.

## Getting Started

### Prerequisites

* Go
* Linux/macOS terminal or another environment capable of running Go

### Start the Server

From the project directory:

```bash
cd server
go build TCPChat.go
./TCPChat [port]
```

For example:

```bash
./TCPChat 8989
```

The server will listen for incoming TCP connections on the selected port.

### Connect as a Client

Using Netcat:

```bash
nc localhost 8989
```

Multiple clients can connect to the same server and communicate through the chat.

## Commands

### Change Username

Inside the chat:

```text
/name new_username
```

## Project Status

This project was completed as part of my full-stack software development studies.

It demonstrates practical experience with TCP networking, concurrent connections, goroutines, synchronization, command-line applications, and client-server architecture.
