---
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# Rebasing & Smart Contracts

OTokens (OETH, Super OETH, and OUSD) use a **rebasing supply** design where yield is reflected by increasing each holder’s token balance rather than by increasing the token’s price. The unit of account remains stable: 1 OUSD = 1 USD and 1 OETH = 1 ETH, while balances rise as underlying assets earn yield. Functionally, this works like interest in a bank account: the value stays constant, the quantity grows.

Yield is realized through **rebases**, which expand token supply proportionally across eligible addresses. Key properties:

* **Rebasing Yield Bonus:** Certain smart contracts (e.g Uniswap liquidity pools) do not support rebasing. Users may chose to forgo rebasing yield to earn DeFi rewards, concentrating rebases to eligible wallets. This improves yield for passive holders, users of wrapped OTokens, and for users deployed in smart contracts where rebasing is enabled.&#x20;
* **Continuous updates:** Rebases are automatically triggered through normal user interactions and by Chainlink Keepers at least once per day. The Guardian contract can also call the `rebase()` function directly on the vault contract to trigger a rebase.
* **Wrapped counterparts:** Each yield-bearing token has a wrapped version (wOETH, wOUSD, etc.) that operates as a ERC-4626 vault.

### Account Behavior: EOAs vs. Smart Contracts

By default, **externally owned accounts (EOAs)** automatically participate in rebasing. Their balances increase whenever a rebase occurs.

**Smart contracts**, including multi-sigs, do **not** rebase automatically. To avoid breaking assumptions in DeFi protocols that expect balances to remain stable unless explicitly updated, OTokens held in contracts default to non-rebasing. This preserves composability with AMMs, lending markets, and other systems.

{% hint style="info" %}
Multi-sig wallets or other smart contracts must call `rebaseOptIn()` to earn yield.
{% endhint %}

Developer notes:

* Governance can whitelist or remotely opt in contracts via onchain proposal (see the Rebase Opt-In Proposal).
* Rebase status for any address can be checked using the `rebaseState(address)` view.

{% hint style="warning" %}
If you are deploying a contract and intend to call `rebaseOptIn()` to earn yield, you cannot call it from the contract's constructor. The contract must be deployed before it can be called.
{% endhint %}

#### Safe Users

[Safe](https://gnosis-safe.io/) users are encouraged to use the [Origin dapp](https://app.originprotocol.com/) which will prompt you to opt-in to receiving yield. If you are using the "old" [Gnosis Wallet](https://github.com/gnosis/MultiSigWallet) or another contract-based wallet, you will need the [proxy contract address](../../registry/contracts/) and the corresponding [ABI](https://api.etherscan.io/api?module=contract\&action=getabi\&address=0x1ae95dd4eeae7ed03da79856c2d44ffa3318f805). Once you add those, you will be able to call the `rebaseOptIn()` function to opt into receiving yield via rebasing or `rebaseOptOut()` to turn it off again.

### Checking Rebase Status

If you are unsure whether or not a particular address will receive yield, you can use a public getter function on the OUSD or OETH contract to check its status.

```solidity
rebaseState(address)
```

This [function](https://github.com/OriginProtocol/origin-dollar/blob/master/contracts/contracts/token/OUSD.sol#L34-L38) returns an integer indicating the current opt-in status _independent of what type of wallet the address belongs to_.

| rebaseState               | Smart contract             | Externally-owned account   |
| ------------------------- | -------------------------- | -------------------------- |
| 0 - NotSet                | **Does not** receive yield | Receives yield             |
| 1 - StdNonRebasing        | **Does not** receive yield | **Does not** receive yield |
| 2 - StdRebasing           | Receives yield             | Receives yield             |
| 3 - YieldDelegationSource | **Does not** receive yield | **Does not** receive yield |
| 4 - YieldDelegationTarget | Receives yield             | Receives yield             |

