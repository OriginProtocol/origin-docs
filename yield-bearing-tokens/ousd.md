# OUSD

### Intro to Origin Dollar&#x20;

Since their introduction in 2014, stablecoins have proven themselves as an ideal way of transferring value without exposing users to the price volatility of free-floating currencies. One of the problems with existing stablecoins is that users must constantly choose between holding an easily spendable coin and earning yield by locking their tokens up in smart contracts.&#x20;

With Origin Dollar (OUSD) holders earn yield with no staking or lockups required. The OUSD smart contract deploys your underlying capital to a diversified set of yield-earning strategies, rebalancing over time to achieve great yields while diversifying risk. Earnings automatically accrue in your wallet and compound continuously while you hold OUSD. There’s no need to unwind complicated positions when you want to spend it. You can transfer it freely without having to pay gas to unlock spendable capital.&#x20;

OUSD also serves as an ideal unit of account. DeFi investors no longer need complicated spreadsheets to calculate their earnings as they can easily see their constantly updated OUSD balances in real-time as their interest compounds automatically. OUSD is an ideal stablecoin for DeFi yield farmers and novice cryptocurrency users alike.

### Core Concepts

Origin's four yield-bearing token products ( [OUSD](ousd.md), [OETH](oeth.md), [Super OETH](super-oeth/), and [OS](os.md)) share most of the same battle-tested code. While each has its own characteristics and use cases, the same overall user experience applies across the product suite. Learn more about the core concepts here:



* [Elastic Supply](core-concepts/elastic-supply.md)
* [Rebasing & Smart Contracts](core-concepts/rebasing-and-smart-contracts.md)
* [Wrapping](core-concepts/wrapping.md)
* [Bridging](core-concepts/bridging.md)
* [AMO](core-concepts/amo.md)
* [Yield Forwarding](core-concepts/yield-forwarding.md)
* [Yield Smoothing](core-concepts/yield-smoothing.md)

### Yield Generation

The protocol is able to generate higher yields than competing protocols due to a combination of important design decisions that amplify the rewards that are returned to OUSD holders:

* Exit fees are returned to the pool, rewarding long-term holders.
* Price oracles favor the collective over the individual, again rewarding long-term holders.
* Smart contracts must manually opt-in to earn yield. This allows the protocol to put more capital to work than would be otherwise possible. For example, the OUSD that is being held on Uniswap does not rebase, but the backing stablecoins are still deployed and earning yield on behalf of OUSD holders.
* Yields tend to get compressed as more funds are deployed into a given strategy. By spreading capital across multiple strategies at once, OUSD is able to deploy more capital with less yield compression.
* The gas costs of harvesting yield are amortized across the entire pool. This makes it economical to harvest more frequently, leading to faster compounding. The more frequent the compounding periods, the faster your money grows.
* The [AMO](https://docs.oeth.com/core-concepts/supported-strategies/curve-metapools) allows the protocol to earn up to 2x the rewards using the same amount of capital.

The net effect of these benefits is that **OUSD is able to consistently return higher yields** than you would get deploying directly into any of the underlying strategies on their own.

### Yield Sources&#x20;

OUSD uses lending, market making and rewards to generate yield:

#### Lending

DeFi money markets enable users to lend and borrow crypto assets without intermediaries, offering greater value for both parties. Lenders earn interest, while borrowers use crypto as collateral to access credit without traditional banking hurdles. These platforms often provide better returns for lenders than traditional markets.

OUSD lends to borrowers with over-collateralized loans, ensuring security through strict liquidation rules. Additionally, platforms like Aave secure lending pools with AAVE tokens to reduce risk further.&#x20;

OUSD exclusively uses top-tier money markets with audited smart contracts and a proven track record of handling hundreds of millions of dollars safely.

One such platform is Morpho Vault, which offers permissionless lending vaults tailored to different risk profiles. OUSD currently lends to the Steakhouse USDC vault, known for its strong yield and institutional-grade risk management.

#### Market Making&#x20;

Automated market makers (AMMs) have quickly risen as the preferred form of decentralized exchange on the Ethereum network. AMMs can only enable new markets when liquidity providers supply liquidity (e.g. multiple tokens for given trading pairs or pools). In return for providing liquidity, liquidity providers are rewarded with trading fees when other users swap tokens. For example, when traders swap two tokens on Uniswap v3, they are currently charged anywhere between 0.05% and 1%. These fees are distributed pro-rata to liquidity providers of the pair based on the percentage of total liquidity that they have provided.

[Impermanent loss](https://medium.com/@pintail/uniswap-a-good-deal-for-liquidity-providers-104c0b6816f2) is an important risk factor to understand, but this concern is largely mitigated by OUSD only providing liquidity for stablecoins of approximately equal value.

The OUSD protocol routes USDT, USDC, and USDS to highly-performing liquidity pools as determined by trading volume and rewards tokens (e.g. Curve rewards CRV tokens to liquidity providers). Yields are then passed on to OUSD holders.

#### Rewards

In addition to collecting interest from lending and fees from market making, the protocol automatically claims and converts the bonus incentives that are being distributed by many of the DeFi protocols. For example, Compound gives away COMP tokens and Curve gives away CRV tokens. These bonus rewards are regularly converted into OUSD and distributed to holders in the form of additional yield. Today, rewards are a significant factor for yield farmers as they represent a large percentage of their returns.&#x20;

The harvesting of these rewards is completely decentralized and open for anyone to participate. The protocol offers 1% of the claimed rewards as an incentive to whoever is willing to call the function first. You can think of it as a reverse auction, whereby the protocol finds whoever is willing to accept the lowest price for the work that is being performed. View the [Incentivized Harvesting Guide](../guides/incentivized-harvesting-guide.md) for details on how to participate.



<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

### Collateral

It is important to understand that OUSD is only as strong as the stablecoins that are backing it. Any loss to the underlying assets will cause a similar loss to the value of OUSD. Because of this, the protocol goes to great lengths to evaluate each stablecoin before adding as a backing asset, including running each through an in-depth Stablecoin Evaluation Framework.

Currently, OUSD supports the following stablecoins:

* USDT
* USDC
* USDS

None of these stablecoins are perfect, but we selected them because of their widespread usage. While these stablecoins have lost their USD peg on multiple occasions, they have demonstrated resiliency in eventually getting back to their 1 USD targets.

It is important to note that all these stablecoins introduce non-trivial counter-party risk. Tether, in particular, has had well-documented banking troubles and regulatory challenges. In addition, both USDT and USDC have backdoors that grant their issuers the power to freeze money in their holder's wallets. While USDS does not have any direct backdoors, its assets can also be negatively impacted since USDC and USDT are accepted as collateral for minting USDS.

Despite these concerns, there are already billions of dollars betting on the security of these stablecoins. It is possible that additional stablecoins will be added to the protocol over time. Support may also be removed if any of these stablecoins prove to be too unreliable or put OUSD holders' funds in jeopardy.

**Turning FUD into Profit**

March 2023 was the first time we saw a major depegging since the launch of OUSD. After the collapse of Silicon Valley Bank, both USDC and DAI (now USDS) dropped to $0.96. Thankfully, OUSD was designed with the assumption that the backing collateral could drop in value at any time. OUSD has multiple protections in place to protect the protocol in case of a depegging. We were proud to see that these protections protected the vault, maintained a superior peg than either USDC or DAI, and generated record-breaking profits for the protocol during this stressful event.



