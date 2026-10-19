# TCP Simple Message

A simple TCP client/server written in C++ for practicing socket programming. The client and server take turns sending messages to each other over `127.0.0.1:1234`.

- `server.cpp` listens on port 1234 and serves one client at a time.
- `client.cpp` connects to the server on localhost.

Messages use a simple protocol: a 4-byte length header followed by the message body (max 4096 bytes).

## Requirements

- Linux or macOS (uses POSIX socket headers)
- `g++`

## Build

```bash
g++ server.cpp -o server
g++ client.cpp -o client
```

## Test

Open two terminals in the project folder.

**Terminal 1** — start the server:

```bash
./server
```

**Terminal 2** — start the client:

```bash
./client
```

Then take turns:

1. In the **client**, type a word and press Enter.
2. The **server** prints `client says: <word>`. Type a reply there and press Enter.
3. The **client** prints `server says: <reply>`.
4. Repeat, or type `end` in the client to disconnect.

**Notes**

- Messages are single words (input is read up to the first space).
- The client sends first, and both sides wait for each other, so they must alternate.
- After the client disconnects, the server keeps running and waits for a new client. Stop it with `Ctrl+C`.
