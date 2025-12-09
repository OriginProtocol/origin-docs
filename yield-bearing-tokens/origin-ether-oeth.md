# Origin Ether (OETH)

<figure><img src="../.gitbook/assets/OETH Hero Image (1).png" alt=""><figcaption></figcaption></figure>

## Introduction

Origin Ether (OETH) is an Ethereum liquid staking token designed to offer enhanced security, higher yield, and a tighter peg to ETH when compared to other LSTs. This is accomplished through rigorous audits, decentralized validator technology (DVT), and a permissionless redemption mechanism paired with deep exit liquidity.

OETH was launched in May 2023 with 95% of its code forked from [OUSD](https://docs.originprotocol.com/yield-bearing-tokens/ousd). This allowed OETH to inherit years of top-tier audits and a proven track record of securing hundreds of millions of dollars worth of underlying collateral. Since growing to over $100 million of TVL itself and being integrated into top protocols such as Morpho, EigenLayer, and Pendle, OETH has become a widely adopted liquid staking token on Ethereum.

In a sea of commoditized liquid staking tokens, OETH stands out with four clear advantages:

1. **Better risk-adjusted yield:** OETH earns its liquid staking yield from the Ethereum beacon chain using distributed validator technology (DVT). This provides OETH with an open and simple infrastructure for managing Ethereum validators and presents an opportunity to earn incentives from DVT platforms, which are harvested and distributed to OETH holders as additional yield.
2. **Tighter peg to ETH:** LSTs are expected to be stable relative to ETH. As the name implies, liquidity is the core premise of these tokens and any pricing deviation from ETH can be catastrophic. While some are more stable than others, all of the top LSTs have experienced some degree of de-pegging from ETH, resulting in a hidden exit cost for users. OETH holds an extremely tight peg to ETH through a combination of permissionless ETH withdrawals and deep onchain liquidity. Because of the AMO liquidity strategy, OETH sustains a tighter peg to ETH than other LSTs—even those with significantly larger TVL.
3. **Merkle Proof Verification of Beacon Chain Balances:** The latest OETH staking upgrade replaces reliance on third-party oracles with direct **Merkle Proof validation** of Beacon Chain balances. By verifying validator balances onchain through cryptographic proofs derived from Ethereum’s consensus layer, OETH ensures validator accounting is fully transparent and tamper-resistant. This trust-minimized design enhances both security and decentralization, making OETH one of the most verifiable and resilient liquid staking tokens on Ethereum.
4. **Compounding 0x02 Validators:** 0x02 validators introduce a more efficient staking architecture for OETH by enabling **native auto-compounding** and **partial withdrawals**. Instead of relying on offchain scripts or manual operations, rewards are automatically added to the validator balance, increasing total staked ETH without external intervention. At the same time, partial withdrawals allow OETH’s staking strategy to provide faster liquidity without fully exiting a validator, unlocking smoother operations and quicker redemptions

These four core pillars of OETH make it the ideal building block for DeFi integrations. By generating the best risk-adjusted yield and maintaining the tightest peg to ETH, OETH allows other protocols to confidently plug into a secure and scalable yield source for their products to leverage.

## Core Concepts

Origin's four yield-bearing token products ( [OUSD](origin-dollar-ousd.md), [OETH](origin-ether-oeth.md), [Super OETH](super-oeth-superoethb.md), and [OS](os.md)) share most of the same battle-tested code. While each has its own characteristics and use cases, the same overall user experience applies across the product suite. Learn more about the core concepts here:

* [Rebasing & Smart Contracts](core-concepts/rebasing-and-smart-contracts.md)
* [Wrapping](core-concepts/wrapping.md)
* [AMO](core-concepts/amo.md)
* [Yield Forwarding](core-concepts/yield-forwarding.md)
* [Yield Smoothing](core-concepts/yield-smoothing.md)

## **Redemptions**

As a permissionless protocol with no gatekeepers, OETH supports redemption by anyone at any time. While there are three different ways to exit OETH, users can go through the [Origin dapp](https://app.originprotocol.com/) to get the best outcome without needing to consider every option.

1. **Async withdrawals** - As with most leading LSTs, OETH offers the ability to request and claim the underlying ETH from the Beacon Chain at any time through a withdrawal queue. This feature provides a fallback in the event that onchain liquidity is insufficient to support a large scale swap with low slippage. Direct redemptions ensure that all of the protocol’s staked ETH is redeemable, with timing determined by Ethereum’s Beacon Chain withdrawal queue.
2. **DEX swap** - The OETH/ETH Curve pool features deep exit liquidity allowing anyone to swap OETH for ETH at the current spot price. This rate fluctuates based on market demand but is often arbitraged back to near 1:1 anytime it falls due to users’ ability to redeem OETH 1:1 via the Origin dapp.
3. **Instant vault redemption** - The OETH vault's legacy `redeem` function takes any amount of OETH and burns it in exchange for WETH at a rate of 1:0.999. This fee of 0.1% protects the protocol from any malicious attacks that could theoretically result from rounding errors. While this redemption feature limits the downside for anyone holding OETH, it is expected to be deprecated as the OETH ARM scales up. With the advent of 1:1 redemptions - both instant and async - vault redemptions are no longer beneficial for users.

Redemption is a critical feature for any LST and is paramount for OETH to remain the optimal building block for DeFi protocols. Allowing users to confidently hold OETH knowing they can exit at virtually 1:1 for ETH anytime will always be OETH's top priority.

## **Zapper**

The OETH Zapper is a convenience contract enabling depositors to use Ether (ETH) to mint OETH or wOETH. The OETH _Vault_ supports WETH but does not allow direct minting with ETH. This design decision increases security and also reduces the gas costs associated with minting.

#### **Zapping**

The [Origin dapp](https://app.originprotocol.com/) supports zapping and minting OETH in a single transaction. Users who come to the dapp with ETH will have their transactions automatically routed to the most economically advantageous contract, whether it’s swapping ETH for OETH via Curve or minting OETH by depositing ETH into the Zapper and subsequently WETH into the Vault automatically.

#### **Withdrawing**

The Zapper contract currently only supports depositing, but any OETH minted via the Zapper is still fully liquid. OETH can be redeemed 1:1 for ETH at any time (see [Core Concepts](https://docs.originprotocol.com/yield-bearing-tokens/core-concepts) for more details).
