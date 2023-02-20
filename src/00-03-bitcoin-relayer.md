# Bitcoin Relayer

Relayer nodes carry data between the Bitcoin blockchain and the Nomic blockchain. You can help support the health of the network by running a Bitcoin node alongside your Nomic node and running the relayer process.

### 1. Sync a Bitcoin node

Download Bitcoin Core: [https://bitcoin.org/en/download](https://bitcoin.org/en/download)

Run it with:
```bash
# mainnet
bitcoind -server -rpcuser=satoshi -rpcpassword=nakamoto

# testnet
bitcoind -server -testnet -rpcuser=satoshi -rpcpassword=nakamoto
```

**NOTE:** To save on disk space, you may want to configure your Bitcoin node to prune block storage. For instance, add `-prune=5000` to only keep a maximum of 5000 MB of blocks. You may also want to use the `-daemon` option to keep the node running in the background.

### 2. Run the relayer process

```bash
# mainnet
nomic relayer --rpc-port=8332 --rpc-user=satoshi --rpc-pass=nakamoto

# testnet
nomic relayer --rpc-port=18332 --rpc-user=satoshi --rpc-pass=nakamoto
```

Leave this running - the relayer will constantly scan the Bitcoin and Nomic chains and broadcast relevant data.

The relayer will also create a server which listens on port 9000 for clients to announce their deposit addresses. To help make the network more reliable, if you run a relayer please open this port and let us know your node's address in Discord or a Github issue so we can have clients make use of your node. If you're going to make this service public, putting the server behind an HTTP reverse proxy is recommended for extra safety.
