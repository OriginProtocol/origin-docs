# Origin Dollar (OUSD)

<figure><img src="../.gitbook/assets/origin dollar (4).png" alt=""><figcaption></figcaption></figure>

## Introduction

Origin Dollar (OUSD) launched in 2020 as Origin’s first yield-bearing token and the first liquid, yield-accruing stablecoin in DeFi. OUSD is designed to earn yield automatically while remaining fully liquid at all times.

OUSD is 100% backed by USDC. The protocol deploys USDC collateral into conservative onchain strategies on Morpho and Curve. As these strategies generate yield, OUSD’s rebasing supply design increases each holder’s balance directly in their wallet without needing to stake, lock tokens, or manually compound rewards.

You can hold OUSD, spend it, or transfer it without unwinding positions. OUSD behaves like a normal stablecoin in your wallet while continuously earning onchain yield in the background.

## Core Concepts

Origin's four yield-bearing token products ( [OUSD](origin-dollar-ousd.md), [OETH](origin-ether-oeth.md), [Super OETH](super-oeth.md), and [OS](origin-sonic-os.md)) share most of the same battle-tested code. While each has its own characteristics and use cases, the same overall user experience applies across the product suite. Learn more about the core concepts here:

* [Rebasing & Smart Contracts](core-concepts/rebasing-and-smart-contracts.md)
* [Wrapping](core-concepts/wrapping.md)
* [AMO](core-concepts/amo.md)
* [Yield Forwarding](core-concepts/yield-forwarding.md)
* [Yield Smoothing](core-concepts/yield-smoothing.md)

## **Yield Generation**

The protocol is able to generate higher yields than direct deposits to underlying protocols due to a combination of important design decisions that amplify the rewards that are returned to OUSD holders:

* **Yield Bonus from Origin’s rebasing dynamic:** Smart contracts must manually opt-in to earn yield. Contracts that do not opt in to earn yield forfeit rewards to normal holders. For example, the OUSD that is being held on Uniswap does not rebase, but the USDC backing is still deployed and earning yield on behalf of other OUSD holders.
* **Yield Diversification:** Yields tend to compress as more funds are deployed into a given strategy. By spreading capital across multiple Morpho markets and Curve liquidity provision, OUSD is able to deploy more capital with less yield compression.
* **Gas Fee Amortization:** The gas costs of harvesting yield are amortized across the entire pool. This makes it economical to harvest more frequently, leading to faster compounding. The more frequent the compounding periods, the faster your money grows.
* **Exit Fees:** When users redeem OUSD on the Origin dapp, the 0.25% exit fee is returned to the pool, which is distributed as yield to OUSD holders.
* **Capital Efficiency:** The [AMO](https://docs.oeth.com/core-concepts/supported-strategies/curve-metapools) allows the protocol to earn up to 2x the rewards using the same amount of capital.

The net effect of these benefits is that **OUSD is able to consistently return higher yields** than you would get deploying directly into any of the underlying strategies on their own.

## Yield Sources

OUSD uses lending on Morpho and liquidity provision on Curve to generate yield:

#### **Lending**

OUSD lends to borrowers with over-collateralized loans, ensuring security through strict liquidation rules. OUSD routes a significant portion of its USDC collateral to Morpho markets, earning lending APYs from and exclusive Morpho vault curated by Origin and Yearn. These vaults are known for their strong yield and institutional-grade risk management.

#### Liquidity Provision

Origin Dollar routes a portion of its USDC collateral to highly-performing Curve pools as determined by trading volume and rewards tokens (e.g. Curve rewards CRV tokens to liquidity providers). Fees generated through liquidity provision are passed on to OUSD holders as yield.

In addition to collecting interest from lending and trading fees from liquidity provision, the protocol automatically claims and converts additional CRV incentives that are being distributed by Curve. Curve incentivizes liquidity pools with CRV tokens, and the rewards routed to the OUSD/USDC pool are regularly converted into OUSD and distributed to holders in the form of additional yield.

{% hint style="info" %}
On November 7th 2025, a [proposal](https://snapshot.org/#/s:origingov.eth/proposal/0x17b2f0e9f609297c926f004e4f5c7704a03b2123a6a2ba82cd4ee63fc82ee25c) passed to simplify OUSD collateral from 3 stablecoin to just 1: USDC.&#x20;
{% endhint %}



