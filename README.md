# raft-kv-cpp

A distributed key-value store in C++ powered by the Raft consensus algorithm. Built to simulate real-world challenges in distributed systems—leader election, fault tolerance, data consistency, and reliable client access.

## 📌 Project Overview

Distributed services demand consistent and available data across multiple nodes—even when failures occur. This project reflects that need: it implements a fully functional Raft-based KV store in C++, complete with:

- Leader election and failure recovery: Nodes can coordinate, choose a leader, and continue serving requests even if peers fail.
- Log replication and consistency: Ensures all nodes agree on operation order, providing a consistent view of data.
- In-memory storage with SkipList: Supports efficient ordered operations, serving as a core data structure.
- RPC-based node communication: Uses Protocol Buffers and Muduo for efficient, type-safe interactions.
- Configurable cluster deployment: Easily spin up multi-node Raft clusters using configuration files.
- Interactive CLI testing: Run PUT/GET commands and observe cluster behavior in real time.

## 🚀 Features

- Full Raft protocol: leader election, heartbeat, log replication, safety guarantees
- In-memory SkipList KV store with ordered operations
- RPC framework powered by Protocol Buffers + Muduo
- Cluster startup via `.conf` files—support for 3+ nodes
- CLI sample: test PUT/GET commands, observe leader/follower behavior in console logs

## 🧱 Project Structure

```bash
.
├── src/                      # Source code
│   ├── raft/                 # Raft consensus logic
│   ├── kv/                   # KV engine
│   ├── rpc/                  # RPC interfaces and services
│   └── main/                 # Entry points for provider, consumer, raft
├── bin/                      # Output binaries
├── proto/                    # .proto files for RPC
├── test.conf                 # Sample config file for Raft nodes
└── docs/                     # Project documentation and images
```

## 🛠️ Requirements

- C++17+
- [Muduo Network Library](https://github.com/chenshuo/muduo)
- Boost
- Protocol Buffers (`protoc`)
- CMake

```bash
# Install dependencies (Ubuntu)
sudo apt-get install libboost-all-dev protobuf-compiler libprotobuf-dev
```

## ⚙️ Build & Run

### 1. Clone and compile

```bash
git clone git@github.com:zhangxijing97/raft-kv-cpp.git
cd raft-kv-cpp
mkdir build && cd build
cmake ..
make
```

### 2. Run Raft Cluster

```bash
cd bin
./raftCoreRun -n 3 -f test.conf
```

You should see output from Raft nodes electing a leader and syncing logs.

### 3. Run RPC Sample (Optional)

```bash
./provider
# In another terminal
./consumer
```

### 4. Run KV Client (Optional)

```bash
./callerMain
```

## 📄 Documentation

- Raft logs and messages are printed in the terminal for each node.
- Configurations are handled by `test.conf` in the `bin/` directory.
- You can find design diagrams and RPC interface examples in the `docs/` folder.

## 🙌 Acknowledgments

Inspired by the [KVstorageBaseRaft-cpp](https://github.com/youngyangyang04/KVstorageBaseRaft-cpp) project and the "CodeThinking" distributed systems series.