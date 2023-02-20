# Setup

### Requirements

- &gt;= 4GB RAM
- &gt;= 100GB of storage
- Linux or macOS _(Windows support coming soon)_

### 1. Build Nomic

Start by building Nomic - for now this requires Rust nightly.
Install rustup if you haven't already:
```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
Install nightly as well (nomic currently requires rust nightly):
```
rustup default nightly
```

Install required dependencies (Ubuntu):
```
sudo apt install build-essential libssl-dev pkg-config clang
```

For systems running Fedora:
```
sudo dnf install clang openssl-devel && sudo dnf group install "C Development Tools and Libraries"
```

Clone the repo and switch to the correct directory and branch:
```
git clone https://github.com/nomic-io/nomic.git
cd nomic
git checkout testnet
```

Build and install. This adds a `nomic` command to your PATH:
```
cargo install --locked --path .
nomic --version
```

### 2. Run your node
Start your Nomic node:
```
# stakenet
nomic start --network mainnet

# testnet
nomic start --network testnet
```

This will run the Nomic state machine and a Tendermint process. For new nodes, the state-sync process will run automatically to get the node up to speed with the current chain.
