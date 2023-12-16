# Masa Oracle: Decentralized Data Protocol 🌐🚀: Testnet Release

The Masa Oracle provides infrastructure for accessing, sharing, and rewarding providers of behavioral, personal, and identity data in a decentralized and private way. The Masa Oracle guarantees transparency, security, and equitable compensation for nodes participating in the Masa zk-Data Network & Marketplace.

## Requirements for Running Masa-Node on Fly.io 📋

To run the `masa-node` on Fly.io's free plan, your server should meet the following specifications:

- **Operating System**: Linux-based OS (Ubuntu 20.04 recommended)
- **Processor**: 4 x Shared CPU
- **Memory**: 1GB RAM
- **Storage**: 20GB SSD
- **Network**: Shared network resources

### Update packages

    apt update
    apt upgrade
  
### Install GO
  
    cd $HOME
    ! [ -x "$(command -v go)" ] && {
    VER="1.20.3"
    wget "https://golang.org/dl/go$VER.linux-amd64.tar.gz"
    sudo rm -rf /usr/local/go
    sudo tar -C /usr/local -xzf "go$VER.linux-amd64.tar.gz"
    rm "go$VER.linux-amd64.tar.gz"
    [ ! -f ~/.bash_profile ] && touch ~/.bash_profile
    echo "export PATH=$PATH:/usr/local/go/bin:~/go/bin" >> ~/.bash_profile
    source $HOME/.bash_profile
    }
    [ ! -d ~/go/bin ] && mkdir -p ~/go/bin

### Installation

1. Clone the repository:
   
   ```bash
   git clone https://github.com/masa-finance/masa-oracle-go-testnet.git
   cd masa-oracle-go-testnet
   ```

 3. Build the node executable:
   
   ```bash
   go build -v -o masa-node ./cmd/masa-node
   ```

## Staking Tokens 🔐

To participate in the network and earn rewards, you must first stake your tokens:

1. Start your node to get Private Key
   ```bash
   ./masa-node --start
   ```
   
2. Get your private key from the node
   ```bash
   cat /root/.masa/masa_oracle_key.ecdsa
   ```

3. Import the private key into Metamask to access your Ethereum address.

4. Send Sepolia ETH and Masa testnet tokens to your address. Then stake!:
   ```bash
   ./masa-node --stake 100
   ```

## Running the Node 🚀

Start your node and join the Masa network with default configurations:
```bash
./masa-node --start
```

## Deploying a Node using Fly.io 🛫

Deploy a node using Fly.io by setting up your environment and configuring your deployment settings:

### Fly.io istallation

1. Istall Fly.io
   
   ```bash
   curl -L https://fly.io/install.sh | sh
   ```

2. Move Fly.io Foldet

   ```bash
   mv /root/.fly /root/masa-oracle-go-testnet/  
   ```
### Register you account on https://fly.io/dashboard

### Setup

1. link your node to the FLY platform

    ```bash
    .fly/bin/flyctl auth login 
    ```
  
2. Run your application with Fly.io from the `masa-oracle-go-testnet` project directory.
   ```bash
   .fly/bin/flyctl launch
   ```
3. Change your node name on the web.

4. Visit your Fly.io profile ,go to your application in the dashboard and in the secrets section specify your node name and private key

5. You can also monitor the status of your node from the monitoring directory

### Checking Deployment Status

1. Check the status of your deployment`:

```bash
.fly/bin/flyctl status -a testmasa
```

