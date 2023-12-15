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
[git clone https://github.com/masa-finance/masa-oracle-testnet](https://github.com/masa-finance/masa-oracle-go-testnet.git
cd masa-oracle-go-testnet
```

## Staking Tokens

🔐 To participate in the network and earn rewards, you must first stake your tokens:

You need to get Sepolia ETH and Masa tokens into your nodes ethereum address. The ethereum address private key is created when you run the node for the first time using ```./masa-node --start``` and is saved locally:
```bash
/Users/{USER}/.masa/masa_oracle_key.ecdsa
```
You can display your private key and then import into Metamask to get your ethereum address by using:
```bash
cat /Users/{USER}/.masa/masa_oracle_key.ecdsa
```
Now send Sepolia ETH and Masa testnet tokens to your address, then you can stake!:
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

## Deploying a Node using Fly.io

To deploy a node using Fly.io, you'll need to set up your environment and configure your deployment settings. Here's a step-by-step guide:

### Prerequisites

- You must have generated a key and stake tokens by running the node locally on your machine using ```./masa-node --start.``` and ```./masa-node --stake 100``` as outlined above 👆🏼👆🏼👆🏼
- Install `flyctl`, the Fly.io command-line tool, following the instructions on the [official Fly.io documentation](https://fly.io/docs/getting-started/installing-flyctl/).
- Sign up for a Fly.io account if you haven't already.
- Log in to Fly.io using ```fly auth login```

### Setup

1. Initialize your application with Fly.io using the `fly launch` command from the `masa-oracle-go-testnet` project directory. This will load the Fly.io `fly.toml` configuration file in your project directory that is pre-configured and build the node using the `Dockerfile`. Please rename your app or fly will rename it for you. **You will have to set a public IPV4 IP Address for UDP to work**
   ```bash
   fly launch
   ```

2. Fly.io uses environment variables to manage secrets. You'll need to set the `PRIVATE_KEY` environment variable to the value of your private key that was used to `--stake` your tokens locally. First, retrieve your private key from the local file that you used to `--stake` your Masa tokens locally:
   ```bash
   cat /Users/{USER}/.masa/masa_oracle_key
   ```
   This command will print the content of your private key file to the console. **It is important that you do not use the ECDSA Ethereum formatted private key in this step!**

3. Next, set this private key as a secret in your Fly.io application. Replace `YOUR_APP_NAME` with the name of your Fly.io application, and `PRIVATE_KEY` with the content of your private key that you retrieved in the previous step:
   ```bash
   fly secrets set -a YOUR_APP_NAME PRIVATE_KEY="PRIVATE_KEY"
   ```
   This command sets the `PRIVATE_KEY` environment variable to your private key in the context of your Fly.io application.

### Deployment

Once your environment is set up, you can deploy your application using the `fly deploy` command:
   ```bash
   fly deploy
   ```
   This command will build and deploy your application to Fly.io.

### Checking Deployment Status

You can check the status of your deployment using the `fly status` command:
   ```bash
   fly status -a YOUR_APP_NAME
   ```
   This command will display the current status of your Fly.io application.

Remember to replace `YOUR_APP_NAME` with the name of your Fly.io application in all the commands.

For more information, refer to the [official Fly.io documentation](https://fly.io/docs/getting-started/).
---
After setting up, your node's address will be displayed, indicating it's ready to connect with other Masa nodes. Follow any additional configuration steps and best practices as per your use case or network requirements.
