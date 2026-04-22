# Origin Dollar (OUSD)

<figure><img src="../.gitbook/assets/origin dollar (10).png" alt=""><figcaption></figcaption></figure>

## Introduction to OUSD&#x20;

Origin Dollar (OUSD) launched in 2020 as Origin’s first yield-bearing token and the first liquid, yield-bearing stablecoin in DeFi. OUSD is designed to earn yield automatically while remaining fully liquid at all times.

OUSD is 100% backed by USDC. The protocol deploys USDC collateral into conservative onchain strategies on Morpho and Curve. As these strategies generate yield, OUSD’s rebasing supply design increases each holder’s balance directly in their wallet without needing to stake, lock tokens, or manually compound rewards.

You can hold OUSD, spend it, or transfer it without unwinding positions. OUSD behaves like a normal stablecoin in your wallet while continuously earning onchain yield in the background.

### **Yield Generation**

The protocol is able to generate higher yields than direct deposits to underlying protocols due to a combination of important design decisions that amplify the rewards that are returned to OUSD holders:

* **Yield Bonus from Origin’s rebasing dynamic:** Smart contracts must manually opt-in to earn yield. Contracts that do not opt in to earn yield forfeit rewards to normal holders. For example, the OUSD that is being held on Uniswap does not rebase, but the USDC backing is still deployed and earning yield on behalf of other OUSD holders.
* **Yield Diversification:** Yields tend to compress as more funds are deployed into a given strategy. By spreading capital across multiple Morpho markets and Curve liquidity provision, OUSD is able to deploy more capital with less yield compression.
* **Gas Fee Amortization:** The gas costs of harvesting yield are amortized across the entire pool. This makes it economical to harvest more frequently, leading to faster compounding. The more frequent the compounding periods, the faster your money grows.
* **Capital Efficiency:** The [AMO](https://docs.originprotocol.com/yield-bearing-tokens/core-concepts/amo) allows the protocol to earn up to 2x the rewards using the same amount of capital.

The net effect of these benefits is that **OUSD is able to consistently return higher yields** than you would get deploying directly into any of the underlying strategies on their own.

### Yield Sources

OUSD uses lending on Morpho and liquidity provision on Curve to generate yield:

#### **Lending**

OUSD lends to borrowers with over-collateralized loans, ensuring security through strict liquidation rules. OUSD routes a significant portion of its USDC collateral to Morpho markets, earning lending APYs from and exclusive Morpho vault curated by Origin and Yearn. These vaults are known for their strong yield and institutional-grade risk management.

#### Liquidity Provision

Origin Dollar routes a portion of its USDC collateral to highly-performing Curve pools as determined by trading volume and rewards tokens (e.g. Curve rewards CRV tokens to liquidity providers). Fees generated through liquidity provision are passed on to OUSD holders as yield.

In addition to collecting interest from lending and trading fees from liquidity provision, the protocol automatically claims and converts additional CRV incentives that are being distributed by Curve. Curve incentivizes liquidity pools with CRV tokens, and the rewards routed to the OUSD/USDC pool are regularly converted into OUSD and distributed to holders in the form of additional yield.

{% hint style="info" %}
On November 7th 2025, a [proposal](https://snapshot.org/#/s:origingov.eth/proposal/0x17b2f0e9f609297c926f004e4f5c7704a03b2123a6a2ba82cd4ee63fc82ee25c) passed to simplify OUSD collateral from 3 stablecoin to just 1: USDC.&#x20;
{% endhint %}

### Redemptions

OUSD can be redeemed 1:1 for USDC on the Origin dapp. For smaller swaps, users can instantly exit with low slippage on Curve and other AMMs – the [OUSD swap form](https://app.originprotocol.com/#/ousd/) on the Origin Dapp will automatically route OUSD to USDC swaps through the most efficient swap route currently available.&#x20;

For direct redemptions, users can redeem OUSD for USDC via the [Origin Dapp.](https://app.originprotocol.com/#/ousd/redeem) When the OSUD Vault  has enough liquidity to process redemptions, users will receive USDC after a 10 minute delay. In the event the vault needs additional liquidity to process the redemption, the redemption process may take up to 24 hours to process.&#x20;

### Performance Fee

Origin charges a 20% performance fee on yield generated on OUSD. This fee is deducted from gross yield before distributions are made to depositors; it does not apply to principal. All fees collected are directed entirely to OGN buybacks, which flow to xOGN stakers, creating a direct link between protocol revenue and token holder value. The APYs displayed on Origin's analytics dashboard and third-party tracking platforms reflect net returns after this fee has been applied, so the figures represent what depositors actually earn.

