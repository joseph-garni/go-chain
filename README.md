# Go Blockchain Project

## Overview
This project implements a simple blockchain in Go, designed to demonstrate the fundamental concepts of blockchain technology through practical code. The implementation creates a basic blockchain that records heart rate data (BPM - Beats Per Minute) and exposes HTTP endpoints to interact with the chain.

## Learning Objectives
This project covers the following Go programming concepts:
1. **Go Functions** - Multiple functions handling blockchain operations like hash calculation and block validation
2. **Hashing** - Implementation of SHA256 cryptographic hashing for ensuring blockchain integrity
3. **Slices and Data Types** - Working with Go's slice data structure to store the blockchain
4. **GET and POST Requests** - HTTP server implementation that handles GET requests to view the blockchain and POST requests to add new blocks

## Features
- Creation of a genesis block on startup
- Adding new blocks with BPM (Beats Per Minute) data
- Block validation to ensure chain integrity
- Chain replacement rules to handle conflicts
- RESTful API to interact with the blockchain

## Project Structure
```
├── .env            # Environment variables (including PORT configuration)
├── LICENSE         # License information
├── README.md       # This file
├── go.mod          # Go module definition
├── go.sum          # Go module checksums
└── main.go         # Main application code containing all blockchain logic
```

## Dependencies
- **github.com/davecgh/go-spew/spew** - For pretty printing blockchain data
- **github.com/gorilla/mux** - For HTTP routing
- **github.com/joho/godotenv** - For loading environment variables

## Installation & Setup

1. **Clone the repository**
   ```
   git clone https://github.com/yourusername/go-blockchain.git
   cd go-blockchain
   ```

2. **Configure environment variables**
   
   Ensure your `.env` file contains the necessary configuration:
   ```
   PORT=8080  # Replace with your preferred port number
   ```

3. **Install dependencies**
   ```
   go mod download
   ```

## Running the Application

1. **Start the blockchain server**
   ```
   go run main.go
   ```
   The server will create a genesis block and begin listening on the configured port.

2. **Access the application**
   
   Open your web browser and navigate to:
   ```
   http://localhost:8080  # Replace 8080 with your configured PORT
   ```

## API Endpoints

The application provides two endpoints to interact with the blockchain:

- `GET /` - View the current state of the blockchain
- `POST /` - Add a new block to the chain with BPM data

### Example: Adding a new block
Using curl to add a new block with a BPM of 75:

```bash
curl -X POST -H "Content-Type: application/json" -d '{"BPM":75}' http://localhost:8080
```

## How It Works

1. The blockchain is stored as a slice of Block structures
2. Each Block contains:
   - Index: Position in the blockchain
   - Timestamp: When the block was created
   - BPM: Beats Per Minute data
   - Hash: SHA256 hash of the block's data
   - PrevHash: Hash of the previous block
3. New blocks are validated by:
   - Checking the index is sequential
   - Verifying the previous hash links match
   - Confirming the block's hash is correct
4. When adding blocks, the longest valid chain is always kept

## Extending the Project

Here are some ideas to expand upon this basic implementation:

1. Add a consensus algorithm like Proof of Work
2. Implement peer-to-peer networking
3. Add transaction support
4. Create a frontend interface
5. Implement wallet functionality
6. Add more data types beyond BPM

## License

This project is licensed under the terms of the LICENSE file included in the repository.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Acknowledgments

- This project was inspired by blockchain fundamentals
- Thanks to the Go community for excellent libraries and documentation
- Looking forward to building on this implementation further and exploring the additional areas where blockchain can be implemented
