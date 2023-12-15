# Masa Oracle: Decentralized Data Protocol 🌐🚀: Testnet Release

The Masa Oracle provides infrastructure for accessing, sharing, and rewarding providers of behavioral, personal, and identity data in a decentralized and private way. The Masa Oracle guarantees transparency, security, and equitable compensation for nodes participating in the Masa zk-Data Network & Marketplace.

## Contents
- [Getting Started](#getting-started) 🌟
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Staking Tokens](#staking-tokens) 🔐
- [Running the Node](#running-the-node) 🚀
- [Command-Line Interface (CLI)](#command-line-interface-cli) 💻
- [Configuration](#configuration) 🔧
- [Connecting Nodes](#connecting-nodes) 🔗
- [Deploying a Node using Fly.io](#deploying-a-node-using-flyio) 🛫
- [Updates & Additional Information](#updates--additional-information) 📢

## Getting Started 🌟

### Prerequisites

Before diving in, ensure these prerequisites are installed:
- **Go**: Grab it from [Go's official site](https://golang.org/dl/) 📥.
- **Docker**: Install from [Docker's official docs](https://docs.docker.com/get-docker/) 🐳.

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/masa-finance/masa-oracle-go-testnet.git
   cd masa-oracle-go-testnet
   ```

## Staking Tokens 🔐

To participate in the network and earn rewards, you must first stake your tokens:

1. Obtain Sepolia ETH and Masa tokens for your node's Ethereum address. The address's private key is created when you run the node for the first time using `./masa-node --start` and is saved locally:
   ```bash
   cat /Users/{USER}/.masa/masa_oracle_key.ecdsa
   ```

2. Import the private key into Metamask to access your Ethereum address.

3. Send Sepolia ETH and Masa testnet tokens to your address. Then you can stake!:
   ```bash
   ./masa-node --stake 100
   ```

## Running the Node 🚀

Start your node and join the Masa network with default configurations:
```bash
./masa-node --start
```

## Command-Line Interface (CLI) 💻

Customize your node's behavior with various flags:
```bash
./masa-node --bootnodes=node1,node2,node3 --port=8080 --udp=true --tcp=false --start=true
```

## Configuration 🔧

To use a custom configuration file:
```bash
./masa-node --config=path/to/config.json
```

## Connecting Nodes 🔗

Connect to a specific node in the network:
```bash
./masa-node --bootnodes=/ip4/34.133.16.77/udp/4001/quic-v1/p2p/16Uiu2HAmAEDCYv5RrbLhZRmHXGWXNuSFa7YDoC5BGeN3NtDmiZEb --port=4001 --udp=true --tcp=false --start=true
```

## Deploying a Node using Fly.io 🛫

Deploy a node using Fly.io by setting up your environment and configuring your deployment settings:

### Prerequisites

- Generate a key and stake tokens by running the node locally with `./masa-node --start` and `./masa-node --stake 100` 👆.
- Install `flyctl`, the Fly.io command-line tool, from the [official Fly.io documentation](https://fly.io/docs/getting-started/installing-flyctl/).
- Sign up for and log into your Fly.io account.

### Setup

1. Initialize your application with Fly.io using `fly launch` from the `masa-oracle-go-testnet` project directory.
   ```bash
   fly launch
   ```

2. Set the `PRIVATE_KEY` environment variable in your Fly.io application using the private key from your local node setup.
   ```bash
   fly secrets set -a YOUR_APP_NAME PRIVATE_KEY="PRIVATE_KEY"
   ```

### Deployment

Deploy your application using `fly deploy`:
```bash
fly deploy
```

### Checking Deployment Status

Check the status of your deployment with `fly status`:
```bash
fly status -a YOUR_APP_NAME
```

---

After setting up, your node's address will be displayed, indicating it's ready to connect with other Masa nodes. Follow any additional configuration steps and best practices as per your use case or network