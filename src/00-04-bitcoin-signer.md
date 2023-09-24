# Bitcoin Signer

The funds in the Bitcoin bridge are held in a large multisig controlled by the Nomic validators. If you are a validator with a significant amount of voting power, it is very important that you run a signer.

You can run the signer with:

```
nomic signer
```

This will automatically generate a Bitcoin extended private key and store it at `~/.nomic-stakenet-3/signer/xpriv`. It will also prompt you to submit your public key to the network so you can be added to the multisig. **KEEP THIS KEY SAFE** - similar to your validator private key, it is important to be mindful of this key so that it is never lost or stolen.

Leave this process running, it will automatically sign Bitcoin transactions that the network wants to create.

In the future, we hope for the community to come up with alternative types of signers which provide for extra security, by e.g. airgapping keys, using HSMs, or prompting the user for an encryption key.

### Circuit Breaker

The signer process will automatically halt signing if, over the past 24 hours,
the signatory set has changed too much, or if too much Bitcoin is being
withdrawn from the bridge.

These parameters are tunable:

```
nomic signer

        --max-sigset-change-rate <MAX_SIGSET_CHANGE_RATE>
            Limits the maximum allowed signatory set change within 24 hours

            The Total Variation Distance between a day-old signatory set and the newly-proposed
            signatory set may not exceed this value

            [default: 0.04]

        --max-withdrawal-rate <MAX_WITHDRAWAL_RATE>
            Limits the fraction of the total reserve that may be withdrawn within the trailing
            24-hour period

            [default: 0.04]
```

Tweaking these parameters is a decision that requires careful thought. A future
release will integrate these circuit breaker checks into the protocol itself.
