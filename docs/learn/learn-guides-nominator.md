---
title: Nominator Guides for Polkadot-JS
description: Learn how to bond tokens, nominate validators, and claim staking rewards using Polkadot-JS.
---

<!-- MessageBox -->
<div id="messageBox" class="floating-message-box">
  <p>
    Polkadot-JS is for developers and power users only. If you need help using the Polkadot-JS UI, you can contact the
    <a href="https://support.polkadot.network/support/home" target="_blank" rel="noopener noreferrer">
      Polkadot Support Team.
    </a>
  </p>
  <button class="close-messagebox" aria-label="Close message">✖</button>
</div>

See [this page](./learn-staking.md) to learn about staking.

## Nominate Using Polkadot-JS

!!!info "Video Tutorials"
    - [How to Nominate/Stake](https://youtu.be/FCXC0CDhyS4?t=219)
    - [Staking with a Ledger device and Polkadot-JS](https://youtu.be/7VlTncHCGPc)
    - [Staking with a Ledger device and Ledger Live](https://www.youtube.com/watch?v=jL-N_IWiYVA)

### Bond your Tokens

!!!info "Support Article"
    Read the support article about [How to Bond Tokens and Nominate](https://support.polkadot.network/support/solutions/articles/65000168057-polkadot-js-ui-how-do-i-stake-nominate-on-polkadot-).

On the [Polkadot-JS UI](https://polkadot.js.org/apps) navigate to the "Staking" tab (within the
"Network" menu).

The "Staking Overview" subsection will show you all the active validators and their information -
their identities, the amount of KSM that are staking for them, amount that is their own provided
stake, how much they charge in commission, the era points they've earned in the current era, and the
last block number that they produced. If you click on the chart button it will take you to the
"Validator Stats" page for that validator that shows you more detailed and historical information
about the validator's stake, rewards and [slashes](./learn-offenses.md).

The "Account actions" subsection ([link](https://polkadot.js.org/apps/#/staking/actions)) allows you
to stake and nominate.

The "Payouts" subsection ([link](https://polkadot.js.org/apps/#/staking/payouts)) allows you to
claim rewards from staking.

The "Targets" subsection ([link](https://polkadot.js.org/apps/#/staking/targets)) will help you
estimate your earnings and this is where it's good to start picking favorites.

The "Waiting" subsection ([link](https://polkadot.js.org/apps/#/staking/waiting)) lists all pending
validators that are awaiting more nominations to enter the active validator set. Validators will
stay in the waiting queue until they have enough KSM backing them (as allocated through the
[Phragmén election mechanism](./learn-phragmen.md)). It is possible validator can remain in the
queue for a very long time if they never get enough backing.

The "Validator Stats" subsection ([link](https://polkadot.js.org/apps/#/staking/query)) allows you
to query a validator's stash address and see historical charts on era points, elected stake,
rewards, and [slashes](./learn-offenses.md).

Pick "Account actions" underneath "Network" > "Staking", then click the "+ Nominator" button.

You will see a modal window that looks like the below:

![nominator-update-1](../assets/kusama/kusama_nominator_popup.png)

Select a "value bonded" that is **less** than the total amount of KSM you have, so you have some
left over to pay transaction fees. Transaction fees are currently at least 0.01 KSM, but they are
dynamic based on a variety of factors including the load of recent blocks.

Also be mindful of the reaping threshold - the amount that must remain in an account lest it be
burned. That amount is 0.01 in Kusama, so it's recommended to keep at least 0.1 KSM in your account
to be on the safe side.

Choose whatever payment destination that makes sense to you. If you're unsure, you can choose "Stash
account (increase amount at stake)" to simply accrue the rewards into the amount you're staking and
earn compound interest.

![Payout account selection dropdown with the custom account option highlighted](../assets/payout/01.png)

### Nominate a Validator

!!!info "Support Article"
    Read the support article about [How to Select Validators](https://support.polkadot.network/support/solutions/articles/65000150130-how-do-i-know-which-validators-to-choose-).

You are now bonded. Being bonded means your tokens are locked and could be
[slashed](./learn-offenses.md) if the validators you nominate misbehave. All bonded funds can be
distributed to [multiple validators](../general/chain-state-values.md).
Be careful about the validators you choose since you will be slashed if your validator commits an
[offence](./learn-offenses.md).

Click on "Nominate" on an account you've bonded and you will be presented with another popup asking
you to select some validators.

![Nominating validators](../assets/kusama/kusama_nominator_selection.png)

Select them, confirm the transaction, and you're done - you are now nominating. Your nominations
will become active in the next era. Eras last six hours on Kusama - depending on when you do this,
your nominations may become active almost immediately, or you may have to wait almost the entire six
hours before your nominations are active. You can check how far along Kusama is in the current era
on the [Staking page](https://polkadot.js.org/apps/#/staking).

Assuming at least one of your nominations ends up in the active validator set, you will start to get
rewards allocated to you. In order to claim them (i.e., add them to your account), you must manually
claim them. To initiate a claim, you can do it yourself or have the validator that you staked for
initiate a claim. This is to help optimize the effectiveness and storage of payouts on Kusama. See
the [Claiming Rewards](./learn-staking.md#claiming-staking-rewards) section of the Staking wiki page for
more details.

### Stop Nominating

!!!info "Support Article"
    Read the support article about [How to Stop Nominating & Unbond Tokens](https://support.polkadot.network/support/solutions/articles/65000167902-how-can-i-unstake-my-tokens-again-). See also the support article about [How to Rebond Tokens](https://support.polkadot.network/support/solutions/articles/65000170241-polkadot-js-ui-how-to-rebond-tokens-during-the-unbonding-period).

At some point, you might decide to stop nominating one or more validators. You can always change who
you're nominating, but you cannot withdraw your tokens unless you unbond them.

## Claiming Rewards with Polkadot-JS

Anyone can trigger a payout for any validator, as long as they are willing to pay the transaction
fee. Someone must submit a transaction with a validator ID and an era index. Polkadot will
automatically calculate that validator's reward and distribute the rewards pro rata.

These details are handled for you automatically if you use the
[Polkadot-JS UI](https://polkadot.js.org/apps/#/staking/payout), which also allows you to submit
batches of eras at once.

To claim rewards on Polkadot-JS UI, you will need to be in the "Payouts" tab underneath "Staking",
which will list all the pending payouts for your stashes.

![pending-payouts](../assets/polkadotjs_payout_page.png)

To then claim your reward, select the "Payout all" button. This will prompt you to select your stash
accounts for payout.

![select-payouts](../assets/polkadotjs_payout_popup.png)

Once you are done with payout, another screen will appear asking for you to sign and submit the
transaction.

![transaction-payouts](../assets/polkadotjs_payout_complete.png)

## Using Command-Line Interface (CLI)

Apart from using the Polkadot-JS UI to participate in the staking, you can do all these things in
CLI instead. The CLI approach allows you to interact with the network without using Polkadot-JS.

### Step 1: Install @polkadot/api-cli

We assume you have installed [NodeJS with npm](https://nodejs.org). Run the following command to
install the `@polkadot/api-cli` globally:

```bash
npm install -g @polkadot/api-cli
```

### Step 2: Bond Tokens

!!!info "Controller accounts are deprecated"
    Controller accounts are deprecated. For more information, see [this discussion](https://forum.polkadot.network/t/staking-controller-deprecation-plan-staking-ui-leads-comms/2748).

Executing the following command:

```bash
polkadot-js-api --seed "MNEMONIC_PHRASE" tx.staking.bond CONTROLLER_ADDRESS NUMBER_OF_TOKENS REWARD_DESTINATION --ws WEBSOCKET_ENDPOINT
```

`CONTROLLER_ADDRESS`: An address you would like to bond to the stash account. (Controller accounts
are now deprecated. Refer to
[this discussion](https://forum.polkadot.network/t/staking-controller-deprecation-plan-staking-ui-leads-comms/2748)
for additional context)

`NUMBER_OF_TOKENS`: The number of native tokens (in Plancks) you would like to stake to the network.
For more information, see [this page](../learn/learn-DOT.md).

`REWARD_DESTINATION`:

- `Staked` - Pay into the stash account, increasing the amount at stake accordingly.
- `Stash` - Pay into the stash account, not increasing the amount at stake.
- `Account` - Pay into a custom account that is not the stash (can be a proxy or another type of
  account).
- `Controller` - Pay into the controller account.

Example for Kusama:

```bash
polkadot-js-api --seed "xxxx xxxxx xxxx xxxxx" tx.staking.bond DMTHrNcmA8QbqRS4rBq8LXn8ipyczFoNMb1X4cY2WD9tdBX 1000000000000 Staked --ws wss://kusama-rpc.polkadot.io
```

For wss endpoints see [this page](https://docs.polkadot.com/develop/networks/).

Result:

```bash
...
...
    "status": {
      "InBlock": "0x0ed1ec0ba69564e8f98958d69f826adef895b5617366a32a3aa384290e98514e"
    }
```

You can check the transaction status by using the value of the `InBlock` in
[Subscan](https://www.subscan.io/). Also, you can verify the bonding state under the
[Staking](https://polkadot.js.org/apps/#/staking/actions) page on the Polkadot-JS UI.

### Step 3: Nominate a Validator

To nominate a validator, you can execute the following command:

```bash
polkadot-js-api --seed "MNEMONIC_PHRASE" tx.staking.nominate '["VALIDATOR_ADDRESS"]' --ws WS_ENDPOINT
```

```bash
polkadot-js-api --seed "xxxx xxxxx xxxx xxxxx" tx.staking.nominate '["CmD9vaMYoiKe7HiFnfkftwvhKbxN9bhyjcDrfFRGbifJEG8","E457XaKbj2yTB2URy8N4UuzmyuFRkcdxYs67UvSgVr7HyFb"]' --ws wss://kusama-rpc.polkadot.io
```

After a few seconds, you should see the hash of the transaction, and if you would like to verify the
nomination status, you can check that on the Polkadot-JS UI as well.
