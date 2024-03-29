# Validating

Becoming a validator comes with extra responsibility compared to running a non-validating full node. Your node becomes an authority for producing blocks and a signatory for the Bitcoin held in the bridge.

### 1. Acquiring coins and staking for voting power

First, find your address by running `nomic balance` (for now this must be run on
the same machine as your active full node).

Ask the community for some coins in the [Discord](https://discord.gg/jH7U2NRJKn) and include your address.

Once you have received coins, you can declare your node as a validator and
delegate to yourself with this command:

```bash
nomic declare \
  <validator_consensus_key> \
  <amount> \
  <commission_rate> \
  <max_commission_rate> \
  <max_commission_rate_change_per_day> \
  <min_self_delegation> \
  <moniker> \
  <website> \
  <identity> \
  <details>
```

**IMPORTANT NOTE:** Carefully double-check all the fields since you will not be
able to modify the `commission_max` or `commission_max_change` after declaring. If you make a mistake, you will have to
declare a new validator instead.

- The `validator_consensus_key` field is the base64 pubkey `value` field found
  under `"validator_info"` in the output of [http://localhost:26657/status](http://localhost:26657/status).
- The `identity` field is the 64-bit hex key suffix found on your Keybase
  profile, used to get your profile picture in wallets and block explorers.

For example:

```bash
nomic declare \
  ohFOw5u9LGq1ZRMTYZD1Y/WrFtg7xfyBaEB4lSgfeC8= \
  100000 \
  0.042 \
  0.1 \
  0.01 \
  100000 \
  "Foo's Validator" \
  "https://foovalidator.com" \
  37AA68F6AA20B7A8 \
  "Please delegate to me!"
```

### 2. Run your Bitcoin signer

The funds in the Bitcoin bridge are held in a large multisig controlled by the
Nomic validators. If you are a validator with a significant amount of voting
power, it is very important that you [run a signer.](./00-04-signer.md)
