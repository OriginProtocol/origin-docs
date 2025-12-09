# Origin Sonic (OS)

<figure><img src="../.gitbook/assets/origin sonic (1).png" alt=""><figcaption></figcaption></figure>

## Introduction

Origin Sonic (OS) is a liquid staking token on the Sonic network designed to offer enhanced security, higher yield, and a tighter peg to S when compared to other Sonic LSTs.

OS is designed to unlock the full potential of staking on Sonic while maximizing your ability to earn S rewards—the network’s native token that’s used to secure the network. By holding and using OS in DeFi, you can further enhance yield-earning capabilities through looping, leverage, and yield trading.

**Why OS?**

* **Battle-tested Code:** OS leverages the OUSD and OETH codebase, with over 14 audits and 4+ years in operation.
* **Deep Liquidity**: OS is integrated with Sonic’s top DEXs, with deep liquidity on SwapX.
* **Enhanced Yield**: Take advantage of cutting-edge yield mechanics, including a yield bonus from the OS rebasing mechanism.

OS was launched in January 2025 with 95% of its code forked from [OUSD](https://docs.originprotocol.com/yield-bearing-tokens/ousd), which has been the basis for all of our yield-bearing tokens (OUSD, OETH, Super OETH and now OS). This allows OS to inherit years of top-tier audits and a proven track record of securing hundreds of millions of dollars worth of underlying collateral.

Like OUSD, OETH, and Super OETH before it, OS is a rebasing token with an up-only design. This means users’ OS balance increases with no manual claiming as staking rewards are earned.

### Core Concepts

Given that Origin's four yield-bearing token products ([OUSD](origin-dollar-ousd.md), [OETH](origin-ether-oeth.md), [Super OETH](super-oeth-superoethb.md), and [OS](os.md)) share most of the same battle-tested code, the same overall user experience applies across the product suite. Learn more about the core concepts here:

* [Rebasing & Smart Contracts](core-concepts/rebasing-and-smart-contracts.md)
* [Wrapping](core-concepts/wrapping.md)
* [AMO](core-concepts/amo.md)
* [Yield Forwarding](core-concepts/yield-forwarding.md)
* [Yield Smoothing](core-concepts/yield-smoothing.md)

## **Staking on Sonic**

### Staking

Sonic uses a Proof-of-Stake system that requires validators to hold Sonic S. Validator nodes are critical to the Sonic chain, responsible for validating transactions and creating new blocks in accordance with the consensus protocol. Anyone with at least 1,000,000 S can run their own validator node to earn epoch rewards and transaction fees.

Stakers can delegate S tokens to a validator that participates to the consensus of Sonic. The more stake assigned to the validator, the more often it is chosen to write new transactions, and therefore the more it earns rewards.

Origin Sonic's staking contract delegates S to a subset of active validators on Sonic. Those validators receive rewards from staking every 10 minutes. The rewards are then distributed to holders of OS through its rebasing mechanism.

While Origin has carefully selected and monitored validators, there exists a risk of one or more of the validators being slashed. To combat this, we have distributed staked S across multiple validators, minimizing the slashing impact arising from the actions of any individual validator.

### Withdrawals

Upon withdrawing from a validator there is a 14 day waiting period to be able to claim the funds from the validators. When the OS vault has available S liquidity, users can initiate withdrawals from the Origin Dapp without waiting for validator exits. When S withdrawals require validator exits, there is a 14-day queue before liquidity is available.

## **OS Redemptions**

As a permissionless protocol with no gatekeepers, OS supports redemption by anyone at any time. As of launch, there will be two ways to exit OS:

1. **Async withdrawal** - OS offers the ability to withdraw the underlying S from the Sonic validators at any time through a withdrawal queue. Users can request and claim their S through the [Origin dapp](https://app.originprotocol.com/) by choosing 'Redeem' under 'OS'. Holders of OS can be assured that 100% of the protocol's staked S can be accessed within a matter of hours or days in any market condition.
2. **DEX swap** - The S/OS pool on SwapX features exit liquidity allowing anyone to swap OS for S at the current spot price. This rate fluctuates based on market demand but will likely be arbitraged back to near 1:1 anytime it falls due to a large sale.

Redemption is a critical feature for any LST and is paramount for OS to remain the optimal building block for DeFi protocols on Sonic. Allowing users to confidently hold OS knowing they can exit at virtually 1:1 for S anytime will always be OS's top priority.

