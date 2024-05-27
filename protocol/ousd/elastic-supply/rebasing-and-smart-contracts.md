# Rebasing & Smart Contracts

If you are using a multi-sig wallet or another smart contract wishing to participate in the rebasing aspect of OUSD or OETH you must call the`rebaseOptIn()` function. This only applies to smart contracts as standard EOA wallets are enrolled automatically.

{% hint style="info" %}
Multi-sig wallets or other smart contracts must call`rebaseOptIn()`to earn yield.
{% endhint %}

By default, OUSD and OETH held on smart contracts will not participate in the rebasing nature of the token and will forfeit any yield unless the smart contract explicitly opts in. This increases the composability of these coins within DeFi as many protocols weren't designed with the expectation that balances might change without an account-specific event being emitted. To other DeFi protocols, OUSD and OETH work just like any other normal, well-behaved ERC-20 until you ask it to change. This is a particularly useful attribute for automated market makers (AMMs) like Uniswap, which break when the number of tokens held changes unexpectedly.

Smart contracts must explicitly opt-in to receive yield via the rebasing mechanism. This fixes the issue with the expanding supply on AMMs while still allowing multi-sig wallets and other smart contracts the opportunity to still participate and earn yield.&#x20;

With the launch of OETH, OGN governance is able to whitelist specific addresses to receive yield. This will allow for future integrations with other DeFi protocols that have immutable contracts or are otherwise unable to opt-in to yield themselves.  &#x20;

{% hint style="warning" %}
If you are deploying a contract and intend to call`rebaseOptIn()`to earn yield, you cannot call it from the contract's constructor. The contract must be deployed before it can be called.
{% endhint %}

[Safe](https://gnosis-safe.io/) users are encouraged to use [the Origin dapp](https://app.originprotocol.com) which will prompt you to opt-in to receiving yield. If you are using the "Old" [Gnosis Wallet](https://github.com/gnosis/MultiSigWallet) or another contract-based wallet, you will need the [proxy contract address](../../../contracts/registry/) and the corresponding [ABI](https://api.etherscan.io/api?module=contract\&action=getabi\&address=0x1ae95dd4eeae7ed03da79856c2d44ffa3318f805). Once you add those, you will be able to call the `rebaseOptIn()` function to opt into receiving yield via rebasing or`rebaseOptOut()` to turn it off again.

#### Checking rebase status

If you are unsure whether or not a particular address will receive yield, you can use a public getter function on the OUSD or OETH contract to check its status.

```solidity
rebaseState(address)
```

This function returns [an integer](https://github.com/OriginProtocol/origin-dollar/blob/master/contracts/contracts/token/OUSD.sol#L34-L38) indicating whether or not the address has opted-in (or out) _independent of what type of wallet the address belongs to_.

| rebaseState | Smart contract             | Externally-owned account   |
| ----------- | -------------------------- | -------------------------- |
| 0 - NotSet  | **Does not** receive yield | Receives yield             |
| 1 - OptOut  | **Does not** receive yield | **Does not** receive yield |
| 2 - OptIn   | Receives yield             | Receives yield             |



Per the on-chain [proposal executed on 12/26/23](https://governance.oeth.com/#/71383011691589635543710677825410966722324428905533481831290224502800746995692), OGN governance now has the ability to remotely opt-in third-party smart contracts for integration purposes, with a [rebase-opt-in-proposal.md](../../../guides/governance-templates/rebase-opt-in-proposal.md "mention"). More information can be found on the proposal [Snapshot](https://snapshot.org/#/ousdgov.eth/proposal/0x90d94adfcdd5f2dd5ba4e694cf1a215874f39bc867394e25a292c11dd3356fcb) and [Discord forum discussion](https://discord.com/channels/404673842007506945/1187525253740646441/1187525528211701770).&#x20;
