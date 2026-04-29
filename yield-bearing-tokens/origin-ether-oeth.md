# Origin Ether (OETH)

<figure><img src="../.gitbook/assets/origin ether (25).png" alt=""><figcaption></figcaption></figure>

## Introduction to OETH

Origin Ether (OETH) is an Ethereum liquid staking token designed to offer enhanced security, higher yield, and a tighter peg to ETH when compared to other LSTs. This is accomplished through rigorous audits, decentralized validator technology (DVT), and a permissionless redemption mechanism paired with deep exit liquidity.

OETH was launched in May 2023 with 95% of its code forked from [OUSD](https://docs.originprotocol.com/yield-bearing-tokens/ousd). This allowed OETH to inherit years of top-tier audits and a proven track record of securing hundreds of millions of dollars of underlying collateral. Since growing to over $100 million of TVL itself and being integrated into top protocols such as Morpho, EigenLayer, and Pendle, OETH has become a widely adopted liquid staking token on Ethereum.

In a sea of commoditized liquid staking tokens, OETH stands out with four clear advantages:

**Better risk-adjusted yield:** OETH earns its liquid staking yield from the Ethereum beacon chain using distributed validator technology (DVT). This provides OETH with an open and simple infrastructure for managing Ethereum validators and presents an opportunity to earn incentives from DVT platforms, which are harvested and distributed to OETH holders as additional yield.

{% embed url="https://www.originprotocol.com/assets/videos/oeth-peg.mp4" %}

**Merkle Proof Verification of Beacon Chain Balances:** The latest OETH staking upgrade replaces reliance on third-party oracles with direct **Merkle Proof validation** of Beacon Chain balances. By verifying validator balances onchain through cryptographic proofs derived from Ethereum’s consensus layer, OETH ensures validator accounting is fully transparent and tamper-resistant. This trust-minimized design enhances both security and decentralization, making OETH one of the most verifiable and resilient liquid staking tokens on Ethereum.

{% embed url="https://www.originprotocol.com/assets/videos/merkle-proof.mp4" %}

**Tighter peg to ETH:** LSTs are expected to be stable relative to ETH. As the name implies, liquidity is the core premise of these tokens and any pricing deviation from ETH can be catastrophic. While some are more stable than others, all of the top LSTs have experienced some degree of de-pegging from ETH, resulting in a hidden exit cost for users. OETH holds an extremely tight peg to ETH through a combination of permissionless ETH withdrawals and deep onchain liquidity. Because of the AMO liquidity strategy, OETH sustains a tighter peg to ETH than other LSTs—even those with significantly larger TVL.

**Compounding 0x02 Validators:** 0x02 validators introduce a more efficient staking architecture for OETH by enabling **native auto-compounding** and **partial withdrawals**. Instead of relying on offchain scripts or manual operations, rewards are automatically added to the validator balance, increasing total staked ETH without external intervention. At the same time, partial withdrawals allow OETH’s staking strategy to provide faster liquidity without fully exiting a validator, unlocking smoother operations and quicker redemptions

These four core pillars of OETH make it the ideal building block for DeFi integrations. By generating the best risk-adjusted yield and maintaining the tightest peg to ETH, OETH allows other protocols to confidently plug into a secure and scalable yield source for their products to leverage.

### Validator Infrastructure

OETH's validators run entirely on SSV Network, organized into two clusters with four nodes each, distributed across separate geographic regions to minimize correlated failure risk. The two node operators running these clusters are P2P and PierTwo. As part of the ongoing transition to 0x02 compounding validators, P2P's cluster is being migrated to PierTwo.&#x20;

Upon completion, PierTwo will operate all OETH validators across both clusters, maintaining the same four-node geographic distribution. The use of SSV's distributed validator technology means no single node holds a complete validator key — consensus requires coordination across the cluster, which reduces slashing risk and eliminates single points of failure at the key level.

### wOETH Pricing and Liquidity

wOETH does not use an external price oracle. When supplied to money markets such as Morpho, wOETH is priced using the ERC-4626 vault exchange rate, the onchain redemption rate reflecting how much OETH one wOETH can be unwrapped for at any given moment. This rate is derived directly from the vault contract via the convertToAssets() function and updates continuously as yield accrues.

Because the price is sourced from the vault contract rather than from secondary market activity, it is not subject to TWAP manipulation or spot price attacks. The exchange rate is monotonically increasing and fully verifiable onchain without reliance on any third-party price feed.

wOETH does not maintain dedicated DEX liquidity pools. This is a deliberate design decision: secondary market depth for wOETH would fragment liquidity away from OETH, where the protocol's AMO concentrates exit liquidity for peg maintenance. Instead, wOETH unwraps to OETH instantly at the vault exchange rate through the Origin dapp or directly onchain via the ERC-4626 withdraw() or redeem() functions. The resulting OETH can then be swapped or redeemed through Origin's existing exit paths.

This pricing and liquidity design applies equally to wOUSD, wOS, and wsuperOETHb, all of which share the same ERC-4626 implementation.

### **Redemptions**

As a permissionless protocol with no gatekeepers, OETH supports redemption by anyone at any time. While there are different ways to exit OETH, users can go through the [Origin dapp](https://app.originprotocol.com/) to get the best outcome without needing to consider every option independently.

1. **Async withdrawals** –– up to 8 days. As with most leading LSTs, OETH offers the ability to request and claim the underlying ETH from the Beacon Chain at any time through a withdrawal queue. This feature provides a fallback in the event that onchain liquidity is insufficient to support a large scale swap with low slippage. Direct redemptions ensure that all of the protocol’s staked ETH is redeemable, with timing determined by Ethereum’s Beacon Chain withdrawal queue . Asynchronous redemptions enable anyone to redeem OETH for ETH at a 1:1 rate with no fees.&#x20;
2. **DEX swap** –– instant. The OETH/ETH Curve pool features deep exit liquidity allowing anyone to swap OETH for ETH at the current spot price. This rate fluctuates based on market demand but is often arbitraged back to near 1:1 anytime it falls due to users’ ability to redeem OETH 1:1 via the Origin dapp.

Redemption is a critical feature for any LST and is paramount for OETH to remain the optimal building block for DeFi protocols. Allowing users to confidently hold OETH knowing they can exit at virtually 1:1 for ETH anytime will always be OETH's top priority.

### Performance Fee

Origin charges a 20% performance fee on yield generated on OETH. This fee is deducted from gross yield before distributions are made to depositors; it does not apply to principal. Net protocol fees after operating expenses are directed to OGN buybacks, which flow to xOGN stakers, creating a direct link between protocol revenue and token holder value. The APYs displayed on Origin's analytics dashboard and third-party tracking platforms reflect net returns after this fee has been applied, so the figures represent what depositors actually earn.

### **Zapper**

The OETH Zapper is a convenience contract enabling depositors to use Ether (ETH) to mint OETH or wOETH. The OETH Vault supports WETH but does not allow direct minting with ETH. This design decision increases security and also reduces the gas costs associated with minting.

The [Origin dapp](https://app.originprotocol.com/) supports zapping and minting OETH in a single transaction. Users who come to the dapp with ETH will have their transactions automatically routed to the most economically advantageous contract, whether it’s swapping ETH for OETH via Curve or minting OETH by depositing ETH into the Zapper and subsequently WETH into the Vault automatically.
