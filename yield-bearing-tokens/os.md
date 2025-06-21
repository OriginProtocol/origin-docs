---
layout:
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
---

# OS

**Intro to OS**&#x20;

Origin Sonic (OS) is a liquid staking token on the Sonic network designed to offer enhanced security, higher yield, and a tighter peg to S when compared to other Sonic LSTs.&#x20;

OS is designed to unlock the full potential of staking on Sonic while maximizing your ability to earn Sonic Points—the network’s rewards mechanism that will be used to distribute 190M S tokens. By holding and using OS in DeFi, you can earn a multiplier your Sonic Points, opening the door to future airdrops and exclusive incentives.

**Why OS?**

* **4x Sonic Points Multiplier**: As an LST, OS benefits from Sonic’s priority rewards system, granting a 4x multiplier on Sonic Points compared to non-LST assets.
* **Earn Active and Passive Points**: Use OS in DeFi protocols to accumulate **active points** or simply hold it to generate **passive points**—both count toward maximizing your rewards.
* **Battle-tested Code:** OS leverages the OUSD and OETH codebase, with over 14 audits and 4+ years in operation.
* **Deep Liquidity**: OS is integrated with Sonic’s top DEXs, starting with a flagship pool on SwapX.
* **Enhanced Yield**: Take advantage of cutting-edge yield mechanics, with upcoming AMO support to enhance liquidity and APY.

OS was launched in January 2025 with 95% of its code forked from [ousd.md](ousd.md "mention"), which has been the basis for all of our yield-bearing tokens (OUSD, OETH, Super OETH and now OS). This allows OS to inherit years of top-tier audits and a proven track record of securing hundreds of millions of dollars worth of underlying collateral. \
\
Like OUSD, OETH, and Super OETH before it, OS is a rebasing token with an up-only design.

### Core Concepts

Given that Origin's four yield-bearing token products ( [OUSD](ousd.md), [OETH](oeth/), [Super OETH](super-oeth/), and [OS](os.md)) share most of the same battle-tested code, the same overall user experience applies across the product suite. Learn more about the core concepts here:

* [Elastic Supply](core-concepts/elastic-supply.md)
* [Rebasing & Smart Contracts](core-concepts/rebasing-and-smart-contracts.md)
* [Wrapping](core-concepts/wrapping.md)
* [Bridging](core-concepts/bridging.md)
* [AMO](core-concepts/amo.md)
* [Yield Forwarding](core-concepts/yield-forwarding.md)

## Staking on Sonic

**Staking**

Sonic uses a Proof-of-Stake system that requires validators to hold Sonic S. Validator nodes are critical to the Sonic chain, responsible for validating transactions and creating new blocks in accordance with the consensus protocol. Anyone with at least 1,000,000 Sonic S can run their own validator node to earn epoch rewards and transaction fees.

Stakers can delegate Sonic "S" tokens to a validator that participates to the consensus of Sonic. The more stake assigned to the validator, the more often it is chosen to write new transactions, and therefore the more it earns rewards.

Origin Sonic's staking contract delegates S to a subset of active validators on Sonic. Those validators receive rewards from staking every 10 minutes. The rewards are then distributed to holders of OS through its rebasing mechanism.

While Origin has carefully selected and monitored validators, there exists a risk of one or more of the validators being slashed. To combat this, we have distributed staked S across multiple validators, minimizing the slashing impact arising from the actions of any individual validator.

**Withdrawals**

Upon withdrawing from a validator there is a 14 day waiting period to be able to claim the funds from the validators.

### OS Redemptions

As a permissionless protocol with no gatekeepers, OS supports redemption by anyone at any time. As of launch, there will be two ways to exit OS, with more potentially added in the future.

1. **Async withdrawal** - OS offers the ability to withdraw the underlying S from the Sonic validators at any time through a withdrawal queue. Users can request and claim their S through the  [Origin dapp](https://originprotocol.eth.limo) by choosing 'Redeem' under 'OS'. Holders of OS can be assured that 100% of the protocol's staked S can be accessed within a matter of hours or days in any market condition.&#x20;
2. **DEX swap** - The S/OS pool on SwapX features exit liquidity allowing anyone to swap OS for S at the current spot price. This rate fluctuates based on market demand but will likely be arbitraged back to near 1:1 anytime it falls due to a large sale.

Redemption is a critical feature for any LST and is paramount for OS to remain the optimal building block for DeFi protocols on Sonic. Allowing users to confidently hold OS knowing they can exit at virtually 1:1 for S anytime will always be OS's top priority.

