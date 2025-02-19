# NetCache - A Fast Key-Value Pair Store

## Overview
This project is an educational implementation of a Redis-like in-memory key-value store, built from scratch in C/C++. It covers network programming concepts, event-driven architecture, data structures, and serialization, offering a deep dive into building a scalable, high-performance server.

## Features
- **TCP server implementation** using socket programming
- **Non-blocking I/O** with an event loop
- **Basic CRUD commands**: `GET`, `SET`, `DEL`, `KEYS`
- **Custom binary protocol** for request/response handling
- **Efficient data structures** (hash tables, AVL trees, Sorted Sets)
- **Pipelining support** for improved performance
- **Progressive hashtable resizing** to optimize memory usage

## Getting Started
### Prerequisites
Ensure you have the following installed on your system:
- GCC or Clang (for compiling C++ code)
- Linux (recommended for socket programming compatibility)

### Installation
Clone the repository:
```sh
 git clone https://github.com/your-username/build-your-own-redis.git
 cd build-your-own-redis
```

Compile the server and client:
```sh
 g++ -Wall -Wextra -O2 -g server.cpp -o server
 g++ -Wall -Wextra -O2 -g client.cpp -o client
```

## Usage
### Running the Server
Start the Redis-like server:
```sh
 ./server
```

### Running the Client
Use the client to interact with the server:
```sh
 ./client set key value
 ./client get key
 ./client del key
 ./client keys
```

### Example Session
```sh
$ ./client set mykey hello
(nil)
$ ./client get mykey
(str) hello
$ ./client keys
(arr) len=1
(str) mykey
(arr) end
$ ./client del mykey
(int) 1
$ ./client get mykey
(nil)
```

## Architecture
### 1. **Network Communication**
- Uses **TCP sockets** for client-server communication.
- Implements **non-blocking I/O** with an **event loop**.
- Uses `poll()` for efficient event-driven handling.

### 2. **Command Handling & Protocol**
- Custom **binary protocol** for efficient message parsing.
- Supports **pipelining** for multiple requests per connection.
- Uses structured request handling to process commands.

### 3. **Data Storage**
- **Hash table** for efficient key-value storage.
- **AVL Tree** for sorted set operations (future scope).
- **Progressive resizing** to optimize performance.

## Future Enhancements
- Implement **sorted sets** using AVL trees.
- Support **persistence** (AOF or RDB format similar to Redis).
- Implement **Pub/Sub messaging**.
- Introduce **multi-threading** for better concurrency.

