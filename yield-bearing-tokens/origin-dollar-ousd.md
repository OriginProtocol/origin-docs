---
layout:
  width: default
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
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

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

#### **Morpho Vaults**

OUSD lends USDC on Morpho markets on Ethereum Mainnet, Base, and HyperLiquid. OUSD routes USDC crosschain to find the best risk adjusted yield opportunities, earning lending APYs from Morpho Vaults co-curated by Origin and Yearn. These vaults are known for their strong yield and institutional-grade risk management.

#### Morpho Vault Curation

The OUSD Morpho Vault is co-curated by Origin and Yearn. Origin defines the vault's risk parameters, including market eligibility criteria and allocation ceilings, with ongoing input from Yearn. Within those parameters, Yearn actively manages day-to-day allocations and can adjust market weights unilaterally, provided adjustments remain within agreed bounds. Market eligibility follows a consistent framework: every market included in the vault must demonstrate deep liquidity and be collateralized by blue-chip, audited assets. Each market is independently assessed before inclusion. Current market allocations are published in real time on [Origin's Analytics Dashboard. ](https://analytics.originprotocol.com/ousd/collateral/)

**About Yearn:** Yearn is one of DeFi's longest-running yield optimization protocols, founded in 2020 with no VC +funding and no founder token allocation. Originally a yield aggregator, Yearn has evolved into a protocol with deep + expertise in vault curation — including hourly allocation optimization, continuous monitoring across 20+ DeFi prot +ocols, and onchain supply cap management. As co-curator of the OUSD Morpho Vault, Yearn brings that infrastructure +to bear on the day-to-day allocation decisions that determine OUSD's risk-adjusted yield. More at [yearn.fi.](https://yearn.finance)

#### Utilization Rates & Strategy Rebalancing

OUSD deploys capital into peer-to-peer Morpho lending markets, where withdrawal availability depends on market utilization. When a lending market reaches 100% utilization, meaning all supplied capital is currently borrowed, OUSD cannot withdraw from that market until borrowers repay or new suppliers enter. Yearn monitors utilization across all active markets continuously and reallocates capital to manage this risk. Rebalances are currently executed manually. Automated rebalancing tooling is on the roadmap and will be introduced in a future protocol update.

#### Liquidity Provision on Curve

Alongside Morpho lending, OUSD maintains protocol-owned liquidity on the Curve OUSD/USDC pool. The protocol typically allocates less than 20% of USDC collateral to this position. The Curve AMO serves two purposes: it provides deep instant exit liquidity for OUSD holders who prefer to swap rather than redeem, and it earns LP incentive rewards that compound into OUSD yield alongside Morpho lending returns.

In addition to collecting interest from lending and trading fees from liquidity provision, the protocol automatically claims and converts additional CRV incentives that are being distributed by Curve.&#x20;

### Cross-Chain Yield Architecture

OUSD is an Ethereum mainnet token, but its yield strategies extend beyond Ethereum. Origin Dollar deploys USDC to Morpho Vault instances on Base and HyperLiquid, capturing lending yields that would otherwise be inaccessible to mainnet holders.&#x20;

Yield generated on these chains is bridged back to Ethereum mainnet through Circle's Cross-Chain Transfer Protocol (CCTP), which has undergone rigorous security audits by OtterSec and ChainSecurity. Mainnet OUSD holders receive the blended yield automatically — no bridging, no cross-chain transactions, no additional action required.

### Redemptions

OUSD can be redeemed 1:1 for USDC on the Origin dapp. For smaller swaps, users can instantly exit with low slippage on Curve and other AMMs – the [OUSD swap form](https://app.originprotocol.com/#/ousd/) on the Origin Dapp will automatically route OUSD to USDC swaps through the most efficient swap route currently available.&#x20;

For direct redemptions, users can redeem OUSD for USDC via the [Origin Dapp.](https://app.originprotocol.com/#/ousd/redeem) When the OUSD Vault  has enough liquidity in the buffer to process redemptions, users will receive USDC after a 10 minute delay. In the event the vault needs additional liquidity to process the redemption, the redemption process may take up to 24 hours to process.&#x20;

