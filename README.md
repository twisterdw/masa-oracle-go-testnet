# Masa Oracle: Decentralized Data Protocol 🌐: Testnet Release

The Masa Oracle provides infrastructure for accessing, sharing, and rewarding providers of behavioral, personal, and identity data in a decentralized and private way. The Masa Oracle guarantees transparency, security, and equitable compensation for nodes participating in the Masa zk-Data Network & Marketplace.

## Contents
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Staking Tokens](#staking-tokens)
- [Running the Node](#running-the-node)
- [Command-Line Interface (CLI)](#command-line-interface-cli)
- [Configuration](#configuration)
- [Connecting Nodes](#connecting-nodes)
- [Updates & Additional Information](#updates--additional-information)

## Getting Started

### Prerequisites

Before diving in, ensure these prerequisites are installed:
- **Go**: Grab it from [Go's official site](https://golang.org/dl/).
- **Docker**: Install from [Docker's official docs](https://docs.docker.com/get-docker/).

### Installation

1. Clone the repository:
```bash
[git clone https://github.com/masa-finance/masa-oracle-go-0.2.3-alpha](https://github.com/masa-finance/masa-oracle-go-0.2.3-alpha.git
cd masa-oracle-go-0.2.3-alpha
```

## Staking Tokens

🔐 To participate in the network and earn rewards, you must first stake your tokens:
```bash
./masa-node --stake 100
```
This command initiates the staking process, allowing the staking contract to spend tokens on your behalf and then stakes the specified amount. You must have Sepolia testnet ETH and Masa tokens in order to stake. 

## Running the Node

🚀 To start your node and join the Masa network with default configurations:
```bash
./masa-node --start
```
This command will start the node using the list of bootnodes specified in the configuration file, if available.

## Command-Line Interface (CLI)

Customize your node's behavior with various flags:
```bash
./masa-node --bootnodes=node1,node2,node3 --port=8080 --udp=true --tcp=false --start=true
```
- `--bootnodes=node1,node2,node3`: Connect to specified bootnodes.
- `--port=8080`: Listen on port `8080`.
- `--udp=true`: Enable UDP protocol.
- `--tcp=false`: Disable TCP protocol.
- `--start=true`: Start the node

Defaults are used if flags are not set:

- `bootnodes`: Falls back to `BOOTNODES` env variable or an empty string.
- `port`: Defaults to `portNbr` env variable or `0`.
- `udp`: Defaults to `UDP` env variable or `false`.
- `tcp`: Defaults to `TCP` env variable or `false`.

## Configuration

🔧 To use a custom configuration file:

```bash
./masa-node --config=path/to/config.json
```

The configuration file is a JSON format that includes an array of bootnodes.

## Connecting Nodes

🔗 To connect to a specific node in the network:
```bash
./masa-node --bootnodes=/ip4/34.133.16.77/udp/4001/quic-v1/p2p/16Uiu2HAmAEDCYv5RrbLhZRmHXGWXNuSFa7YDoC5BGeN3NtDmiZEb --port=4001 --udp=true --tcp=false --start=true
```
This will connect your Masa Oracle node to the specified node using the provided multi-address.

---

After setting up, your node's address will be displayed, indicating it's ready to connect with other Masa nodes. Follow any additional configuration steps and best practices as per your use case or network requirements.
