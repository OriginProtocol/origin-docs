# Governance

### Principals

Origin products operate as decentralized protocols governed by a distributed set of stakeholders. Yield generation, fee collection, and fee distribution are executed entirely through smart contracts. Upgrades to these contracts pass through a timelock and can only be initiated through governance controlled by xOGN holders.

Although the initial contracts and strategies were developed by the Origin team, protocol evolution is open to the broader community. Governance participants can propose parameter changes, introduce new strategies, contribute code, or vote on active proposals. The expectation is that major decisions are made collectively, while limited day-to-day responsibilities may be delegated to trusted contributors who maintain the protocol’s operations.

Governance proposals require participation from at least 20% of the xOGN supply to reach quorum. There is no minimum requirement to cast a vote on existing proposals. All approved proposals are executed only after passing through a timelock, ensuring a delay between approval and implementation. This delay provides transparency and allows users to exit positions if a proposal introduces changes they deem unfavorable.

### **Proposal lifecycle**

Changes to Origin’s smart contracts require onchain proposals to be created, approved, and executed by governance token holders. All pending and historical onchain proposals are visible on the governance page of the [Origin Dapp](https://app.originprotocol.com/).

Initiating this type of formal, binding proposal requires technical skills and knowledge of the protocol’s code. Onchain proposals also involve transaction costs (gas fees) necessary to update the state of the blockchain. As a result, most proposals go through an informal, off-chain process occurring on the [Origin Protocol Snapshot Space](https://snapshot.org/#/origingov.eth).

Snapshot enables any eligible governance token holder to create a proposal or vote at no cost. This also reduces the complexity and expense required to make a proposal and allows for the community to signal its approval or opposition to a given change. We encourage everyone to propose improvements at any time.

To help stay up to date on Snapshot proposals, you can enable email notifications by visiting [Snapshot V1](https://v1.snapshot.box/#/), clicking on your username, and adding an email.

It’s natural for proposals to be accompanied by healthy debate or discussion regarding implementation, reasoning, methodology, etc. Discussions regarding new proposals now start in the [Origin Governance Forum](https://governance.originprotocol.com/) and are cross-posted to [Origin's Discord server](https://originprotocol.com/discord).

## **Participating**

High-level criteria are required to vote and make proposals:

Hold sufficient xOGN tokens (Staked Origin Tokens)

* No minimum to vote on existing proposals
* 5,000 xOGN to create a Snapshot proposal
* 100,000 xOGN to create an on-chain proposal

(Note, you have the option to delegate your votes to another Ethereum wallet.)

Here are the step-by-step instructions to vote and create a proposal:

1. Obtain OGN from a centralized exchange like Coinbase or Binance, or a decentralized exchange such as Uniswap or Curve.
2. Stake OGN using the [Origin App](https://app.originprotocol.com/#/ogn/staking)
3.  Submit and discuss the proposal on the [Origin Governance Forum](https://governance.originprotocol.com/) and share the link on the [Origin Protocol Discord server](https://originprotocol.com/discord) under the #governance channel for maximum visibility

    _(1-4 weeks of discussion recommended)_
4. Submit the proposal on Snapshot for a signaling vote
5. Vote for the implementation to be executed&#x20;

Feel free to use one of the [templates](../resources/governance-templates/) as a guide for writing governance proposals

#### Here are the parameters currently configured on the governance contract: <a href="#strategists" id="strategists"></a>

| Name                  | Value                      | Description                                                                                                                                                                              |
| --------------------- | -------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Voting delay          | 24 hours                   | How soon the voting period begins following the submission of a proposal - can be used to enforce a delay after a proposal is published for users to buy tokens, or delegate their votes |
| Voting period         | 48 hours                   | The window of time for votes to be cast following the end of the voting delay                                                                                                            |
| Proposal threshold    | 100,000 xOGN               | The minimum number of tokens required for an account to be eligible to submit a proposal                                                                                                 |
| Quorum                | 20% of xOGN supply         | The minimum number of votes needed for a proposal to succeed (assuming a majority of them are in support of the proposal)                                                                |
| Late quorum extension | 11,520 blocks (\~1.6 days) | The amount of time required to pass from when a proposal reaches quorum until its voting period ends                                                                                     |
| Timelock delay        | 172,800 seconds (2 days)   | The minimum amount of time required after the end of the voting period before a proposal can be executed and take effect                                                                 |

## Guardians

\
Some functionality, such as rebalancing funds or pausing deposits, can be triggered without the timelock and with far fewer signers. This allows the Origin team to react more quickly to market conditions or security threats. These signers, known as Guardians, have the ability to execute a limited number of functions with only 2 of 9 signers.

The Guardian multi-sig can do the following actions on the vault:

* depositToStrategy - deposit multiple assets from the vault into the strategy.
* withdrawFromStrategy - withdraw multiple assets from the strategy to the vault.
* setVaultBuffer - adjust the amount of funds held outside strategies for cheaper redeems.
* setAssetDefaultStrategy - which strategy mints and redeems pull from for a particular strategy
* withdrawAllFromStrategy - remove funds from a single strategy and send them to the vault
* withdrawAllFromStrategies - remove funds from all active strategies and send them to the vault
* pauseRebase - pause all rebases
* pauseCapital - pause all mints and redeems
* unpauseCapital - allow all mints and redeems
* swapCollateral - swaps collateral assets sitting in the vault
