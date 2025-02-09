# Cyber_Security
# Secure Messaging System

## Overview
This project implements a secure messaging system using RSA encryption and digital signatures. The system consists of a server and client that communicate using encrypted messages, ensuring both confidentiality and authenticity.

## Features
- RSA Key Generation (2048-bit keys)
- Message encryption using RSA
- Digital signatures for message authentication
- Secure storage and retrieval of messages
- Server-client communication over sockets

## Technologies Used
- Java
- RSA (Java Security API)
- Base64 Encoding/Decoding
- Sockets for networking
- File I/O for key management

## File Structure
```
├── Client.java          # Client-side implementation
├── Server.java          # Server-side implementation
├── RSAKeyGen.java       # Key pair generator
├── server.prv          # Server's private key
├── server.pub          # Server's public key
├── <userID>.prv        # User's private key (generated dynamically)
├── <userID>.pub        # User's public key (generated dynamically)
```

## Setup and Execution
### 1. Generate RSA Keys
Before running the client or server, generate RSA key pairs for each user and the server using:
```sh
javac RSAKeyGen.java
java RSAKeyGen <userID>
java RSAKeyGen server
```
This will create `<userID>.prv`, `<userID>.pub`, `server.prv`, and `server.pub` files.

### 2. Start the Server
Compile and run the server using:
```sh
javac Server.java
java Server <port>
```
Example:
```sh
java Server 8080
```

### 3. Start the Client
Compile and run the client using:
```sh
javac Client.java
java Client <server_hostname> <port> <userID>
```
Example:
```sh
java Client localhost 8080 alice
```

## How It Works
1. The client connects to the server and sends a hashed user ID.
2. The server checks for new messages and sends them securely.
3. Messages are encrypted with RSA and signed using SHA256withRSA.
4. The client verifies the signature and decrypts the message.
5. Users can send encrypted and signed messages to other users.

## Error Handling
- If key files are missing, the program will exit with an error.
- If a signature verification fails, the message is rejected.
- If an encrypted message cannot be decrypted, an error message is displayed.

## Future Improvements
- Implement database storage for persistent message storage.
- Enhance user authentication.
- Add a GUI for better user experience.

## Contributors
- **Om Vilas Shimpi**

