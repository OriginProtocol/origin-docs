# OETH

### Intro to Origin Ether

Origin Ether (OETH) is a liquid ETH staking token designed to offer enhanced security, higher yield, and a tighter peg to ETH when compared to other LSTs. This is accomplished through rigorous audits, decentralized validator technology (DVT), and a permissionless redemption mechanism paired with deep exit liquidity.

OETH was launched in May 2023 with 95% of its code forked from [ousd.md](ousd.md "mention"). This allowed OETH to inherit years of top-tier audits and a proven track record of securing hundreds of millions of dollars worth of underlying collateral. Since growing to over $100 million of TVL itself and being integrated into top protocols such as EigenLayer and Pendle, OETH has transitioned from a yield aggregator to a pure liquid staking token.

In a sea of commoditized liquid staking tokens on Ethereum, OETH stands out with two clear advantages:

1.  **Better risk-adjusted yield**

    OETH earns its liquid staking yield from the Ethereum beacon chain using distributed validator technology (DVT). This provides OETH with an open and simple infrastructure for managing Ethereum validators and presents an opportunity to earn incentives from DVT platforms, which are harvested and distributed to OETH holders as additional yield.&#x20;
2.  **Tighter peg to ETH**

    LSTs are expected to be stable relative to ETH. As the name implies, liquidity is the core premise of these tokens and any pricing deviation from ETH can be catastrophic. While some are more stable than others, all of the top LSTs have experienced some degree of de-pegging from ETH, resulting in a hidden exit cost for users. It's not uncommon to acquire an LST expecting to earn yield at a certain rate only to find out that the yield is effectively lost (or worse) when it's time to withdraw ETH or swap back. OETH strives to be the only LST with a perfect 1:1 peg to ETH. This is accomplished through a combination of permissionless ETH withdrawals and an instant 1:1 redemption integration with the OETH ARM (similar to the [steth-arm.md](../arm/steth-arm.md "mention")).

These two core pillars of OETH make it the ideal building block for DeFi integrations. By generating the best risk-adjusted yield and maintaining the tightest peg to ETH, OETH allows other protocols to confidently plug into a secure and scalable yield source for their products to leverage.

### Core Concepts

Origin's four yield-bearing token products ( [OUSD](ousd.md), [OETH](oeth.md), [Super OETH](super-oeth/), and [OS](os.md)) share most of the same battle-tested code. While each has its own characteristics and use cases, the same overall user experience applies across the product suite. Learn more about the core concepts here:

* [Elastic Supply](core-concepts/elastic-supply.md)
* [Rebasing & Smart Contracts](core-concepts/rebasing-and-smart-contracts.md)
* [Wrapping](core-concepts/wrapping.md)
* [Bridging](core-concepts/bridging.md)
* [AMO](core-concepts/amo.md)
* [Yield Forwarding](core-concepts/yield-forwarding.md)
* [Yield Smoothing](core-concepts/yield-smoothing.md)

### Liquid Staking

ETH staking requires technical expertise, setting up a validator node, and depositing a minimum of 32 ETH. Liquid staking tokens simplify this process by allowing users to stake any amount of ETH and earn yield without running a validator node or meeting the 32 ETH requirement. LSTs are becoming more liquid and stable, boosting their importance in DeFi. However, Lido's 75% market share creates a potential single point of failure, especially under regulatory scrutiny.

OETH offers enhanced decentralization and security of ETH staking through its use of distributed validator technology (DVT) and the [SSV network](https://ssv.network/).

* **Active-Active Redundancy & Fault Tolerance**: SSV's DVT allows OETH to split and distribute a validator key into multiple KeyShares, running the validator across multiple non-trusting nodes. This means if one node goes offline, others can take over, ensuring continuous operation and reducing the risk of slashing. This redundancy leads to a more reliable staking experience, thereby maximizing yield.
* **Non-Custodial & Secure ETH Staking**: SSV technology enables the validator key to be securely generated, split into KeyShares, and stored offline. The distributed nodes then operate the validator without having direct access to the key, ensuring a highly secure staking process. This security attracts more users, increasing the overall staking pool and potential yields.
* **Decentralization & Diversity**: Independent operators worldwide provide the infrastructure for SSV.network. Each operator chooses their validator client software and hardware, while stakers can select their operators. This decentralized approach eliminates single points of failure and risks, promoting a healthy and resilient Ethereum network. A decentralized and robust network enhances staking yields by reducing downtime and slashing incidents.

### Redemption

As a permissionless protocol with no gatekeepers, OETH supports redemption by anyone at any time. While there are four different ways to exit OETH, users can go through the [Origin dapp](https://originprotocol.eth.limo) to get the best outcome without needing to consider every option.

1. **Instant 1:1 ARM swap** - OETH is the first LST to offer lossless 1:1 WETH exchange through Origin's Automated Redemption Manager (similar to the[steth-arm.md](../arm/steth-arm.md "mention")). This mechanism allows anyone to enter and exit OETH instantly with no slippage or price impact. The OETH ARM has recently been deployed to support OETH redemptions at a small scale and will be scaled up with additional liquidity in the coming weeks.
2. **Async withdrawal** - As with most other top tier LSTs, OETH offers the ability to request and claim the underlying ETH from the Beacon Chain at any time through a withdrawal queue. This feature provides a fallback in the event that the OETH ARM has insufficient liquidity to support a large scale instant 1:1 swap. Holders of OETH can be assured that 100% of the protocol's staked ETH can be accessed within a matter of hours or days in any market conditions.
3. **DEX swap** - The OETH/ETH Curve pool features deep exit liquidity allowing anyone to swap OETH for ETH at the current spot price. This rate fluctuates based on market demand but is often arbitraged back to near 1:1 anytime it falls due to a large sale.
4. **Instant vault redemption** - The OETH vault's legacy `redeem` function takes any amount of OETH and burns it in exchange for WETH at a rate of 1:0.999. This fee of 0.1% protects the protocol from any malicious attacks that could theoretically result from rounding errors. While this redemption feature limits the downside for anyone holding OETH, it is expected to be deprecated as the OETH ARM scales up. With the advent of 1:1 redemptions - both instant and async - vault redemptions are no longer beneficial for users.

Redemption is a critical feature for any LST and is paramount for OETH to remain the optimal building block for DeFi protocols. Allowing users to confidently hold OETH knowing they can exit at virtually 1:1 for ETH anytime will always be OETH's top priority.

### Zapper&#x20;

The OETH Zapper is a convenience contract enabling depositors to use Ether (ETH) to mint OETH. The OETH _Vault_ supports WETH but does not allow direct minting with ETH. This design decision increases security and also reduces the gas costs associated with minting.

#### Zapping

The [Origin dapp](https://app.originprotocol.com/) supports zapping and minting OETH in a single transaction. Users who come to the dapp with ETH will have their transactions automatically routed to the most economically advantageous contract, whether it’s swapping ETH for OETH via Curve or minting OETH by depositing ETH into the Zapper and subsequently WETH into the Vault automatically.

#### Withdrawing

The Zapper contract currently only supports depositing, but any OETH minted via the Zapper is still fully liquid. OETH can be redeemed 1:1 for ETH at any time (see [Core Concepts](https://docs.originprotocol.com/yield-bearing-tokens/core-concepts) for more details).
