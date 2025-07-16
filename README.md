# raft-kv-cpp

A lightweight distributed key-value store written in C++, based on the Raft consensus algorithm. This project was built to deepen understanding of distributed systems, leader election, log replication, and in-memory storage using SkipList. It is not intended for production use, but rather as a demonstration of distributed system principles.

## 🚀 Features

- 🔁 Raft-based consensus with leader election and log replication
- 💾 SkipList-based in-memory key-value store
- 📡 Custom RPC communication via Muduo and Protocol Buffers
- 🛠️ Configurable cluster deployment using simple conf files
- 🧪 CLI-based testing with logs and real-time outputs

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
git clone https://github.com/YOUR_USERNAME/raft-kv-cpp.git
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

## 📌 Disclaimer

This project is built for learning and demonstration purposes. It is not production-ready.

## 🙌 Acknowledgments

Inspired by the [KVstorageBaseRaft-cpp](https://github.com/youngyangyang04/KVstorageBaseRaft-cpp) project and the "CodeThinking" distributed systems series.