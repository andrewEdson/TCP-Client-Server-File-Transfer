# TCP Client-Server File Transfer Application

A Python-based TCP client-server application that enables bidirectional file transfer and real-time messaging between multiple clients and a server.

## Features

- **Multi-threaded Server**: Handles multiple client connections simultaneously
- **Bidirectional File Transfer**: Send files from client to server and vice versa
- **Real-time Messaging**: Exchange text messages between client and server
- **TCP Socket Communication**: Reliable data transmission using TCP protocol
- **Interactive CLI**: User-friendly command-line interface for both client and server

## Project Structure

```
HA03/
├── client.py          # Client-side application
├── server.py          # Server-side application
├── client_files/      # Directory for files received by client
│   ├── serverTest.txt
│   ├── test.csv
│   └── test.txt
├── server_files/      # Directory for files received by server
│   ├── serverTest.txt
│   └── test.txt
└── README.md
```

## Requirements

- Python 3.x
- No external dependencies (uses built-in libraries only)
  - `socket`
  - `threading`
  - `os`

## Installation

1. Clone this repository:

```bash
git clone https://github.com/Andrew-Edson/HA03.git
cd HA03
```

2. Ensure you have Python 3.x installed:

```bash
python --version
```

## Usage

### Starting the Server

1. Open a terminal/command prompt
2. Navigate to the project directory
3. Run the server:

```bash
python server.py
```

4. The server will start listening on `127.0.0.1:12345`

### Starting the Client

1. Open a new terminal/command prompt
2. Navigate to the same project directory
3. Run the client:

```bash
python client.py
```

4. The client will automatically connect to the server

### Commands

Once connected, you can use the following commands:

#### Client Commands:

- **Send a message**: Type any text and press Enter
- **Send a file**: Type `FILE` and press Enter, then provide the file path
- **Disconnect**: Type `exit` and press Enter

#### Server Commands:

- **Send a message**: Type any text as a response to client messages
- **Send a file**: Type `FILE` as a response, then provide the file path

## How It Works

### File Transfer Protocol

1. **Client to Server**:

   - Client sends `"FILE"` command
   - Client sends filename
   - Client sends file size
   - Client sends file data in 1024-byte chunks

2. **Server to Client**:
   - Server responds with `"FILE"` to client message
   - Server sends filename
   - Server sends file size
   - Server sends file data in 1024-byte chunks

### File Storage

- Files sent to the server are stored in the `server_files/` directory
- Files sent to the client are stored in the `client_files/` directory

## Example Session

### Server Terminal:

```
Server started
Connection from ('127.0.0.1', 54321)
Client: Hello Server!
Server Response (Input 'FILE' to send a file)
> Hello Client!
```

### Client Terminal:

```
Client connected
Enter Message (Input 'FILE' to send a file) (Input 'exit' to disconnect)
> Hello Server!
Server: Hello Client!
Enter Message (Input 'FILE' to send a file) (Input 'exit' to disconnect)
> FILE
Enter file path: client_files/test.txt
File test.txt sent
```

## Technical Details

- **Protocol**: TCP (Transmission Control Protocol)
- **Server Address**: 127.0.0.1 (localhost)
- **Port**: 12345
- **Buffer Size**: 1024 bytes
- **Threading**: Server uses threading to handle multiple clients
- **Encoding**: UTF-8 for text messages

## Error Handling

- File not found errors are handled gracefully
- Connection errors are managed with proper socket cleanup
- Invalid file paths are validated before transfer

## Limitations

- Server runs on localhost only (127.0.0.1)
- File transfer uses fixed 1024-byte chunks
- No authentication or security features
- Basic error handling implementation

## Future Enhancements

- [ ] Add user authentication
- [ ] Implement file encryption for secure transfer
- [ ] Add progress bars for large file transfers
- [ ] Support for remote server connections
- [ ] GUI interface using tkinter or PyQt
- [ ] File compression before transfer
- [ ] Resume interrupted transfers

## Contributing

This is a CS 455 homework assignment. If you'd like to suggest improvements or report issues, feel free to open an issue or submit a pull request.

## License

This project is created for educational purposes as part of CS 455 coursework.

## Author

Andrew Edson - CS 455 Fall 2024

---

_This project demonstrates fundamental network programming concepts including TCP sockets, multi-threading, and file I/O operations in Python._
