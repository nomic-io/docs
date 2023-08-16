# Upgrading

Nomic has its own unique upgrade system. Once you switch to the latest release, your node will signal its readiness, and the network will automatically switch to the new version once enough voting power has signalled.

To prepare your Nomic Stakenet node for a network upgrade, simply compile the new version then restart:

```bash
cd nomic
git checkout main
git pull
cargo install --path . --locked

# (make sure to kill your existing node first)
nomic start --network testnet --legacy-version 4.1.3
```
