# Governance

**Principles**

Origin Dollar and Origin Ether are decentralized protocols governed by multiple stakeholders around the world. Everything from yield generation to fee collection and distribution is managed by a set of smart contracts on the Ethereum blockchain. These contracts are upgradeable with a timelock and controlled by hundreds of governance token holders. While the initial contracts and yield-earning strategies were developed by the Origin team, anyone can shape the future of the protocol by creating or voting on proposals, submitting new strategies, or contributing code improvements. We intend for all important decisions to be made through community governance and for limited powers to be delegated to trusted contributors who are more actively involved in the day-to-day management of the protocol.

**Proposal lifecycle**

Changes to the Origin Dollar and Origin Ether contracts and the movement of funds require on-chain proposals to be created, approved, and executed by governance token holders. All pending and historical on-chain proposals are visible on the governance page of the Origin Dapp.&#x20;

Initiating this type of formal, binding proposal requires technical skills and knowledge of the protocol’s code. On-chain proposals also involve transaction costs (Ethereum gas) necessary to update the state of the blockchain. As a result, most proposals go through an informal, off-chain process occurring on the [Origin Protocol Snapshot Space](https://snapshot.org/#/origingov.eth). Snapshot enables any eligible governance token holder to create a proposal or vote at no cost. This also reduces the complexity and expense required to make a proposal and allows for the community to signal its approval or opposition to a given change. We encourage everyone to propose improvements at any time.

It’s natural for proposals to be accompanied by healthy debate or discussion regarding implementation, reasoning, methodology, etc. Rather than host these discussions on a separate forum, they currently live in the [Origin Protocol Discord server](https://originprotocol.com/discord) under the #defi-governance-forum channel.

**Participating**

High-level criteria are required to vote and make proposals:

Hold sufficient xOGN tokens (Staked Origin Tokens)

* No minimum to vote on existing proposals
* 5,000 xOGN to create a Snapshot proposal
* 100,000 veOGV to create an on-chain proposal

(Note, you have the option to delegate your votes to another Ethereum wallet.)

Here are the step-by-step instructions to vote and create a proposal:

1. Obtain OGN from a centralized exchange like Coinbase or Binance, or a decentralized exchange such as Uniswap or Curve.
2. Stake OGN using the Origin App
3.  Discuss the proposal in the [Origin Protocol Discord server](https://originprotocol.com/discord)

    _(1-4 weeks of discussion recommended)_
4.  Submit the proposal for a signaling vote

    _(Set the voting period for 1 week for new yield strategies, or 2 weeks for new collateral)_
5. Vote for the implementation to be executed&#x20;

Feel free to use one of the [templates](https://docs.oeth.com/guides/governance-templates) as a guide for writing governance proposals

Routine funds management and precautionary actions are handled by multi-sig signers known as the [Strategists](https://docs.ousd.com/governance/admin-privileges#strategist). These users have been delegated authority to implement reallocations across OUSD’s and OETH's yield-generating strategies in addition to being granted other limited emergency powers. Strategist actions do not require an on-chain vote involving xOGN holders since they are executed from a 2 of 9 multi-sig account. However, they are usually accompanied by an off-chain Snapshot proposal except in rare cases when the Strategists proactively respond to market conditions (e.g. de-risking from a given strategy or collateral type).
