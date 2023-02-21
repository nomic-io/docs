# Upgrading

These steps will prepare your testnet node for the **Feb 2023 testnet upgrade**:

### 1. Build and copy legacy binary

The first step will require you to build and copy an updated version of the pre-upgrade testnet binary. This will enable the new version of nomic to run the current binary until it is time to upgrade, then it will seamlessly switch (similar to `cosmovisor` on Cosmos SDK chains).

```bash
git pull
git checkout testnet-v4d-staging
cargo build --release
cp target/release/nomic ~/.nomic-testnet-4d/nomic-v4
```

###  2. Build and start new binary 

Now we can start the new binary, which will automatically activate the changes once the upgrade time is reached.

```bash
git pull
git checkout testnet
cargo install --path . --locked --features compat
```

```bash
# (make sure to kill your existing testnet node first)
nomic start --network testnet --legacy-version 4.1.3
```

Your node will automatically perform the upgrade on *Thursday, February 23 at 18:00 UTC*.

Until the upgrade time, normal commands such as `nomic balance` will fail. Before then, you can use the legacy binary to execute these commands, e.g.:
```bash
~/.nomic-testnet-4d/nomic-v4 balance
```
