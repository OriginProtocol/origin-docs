# stETH ARM

## stETH ARM: Introduction

Origin’s stETH ARM offers LPs a low-risk strategy to earn passive yield on their ETH. The ARM (Automated Redemption Manager) consists of an ETH vault that is used to arbitrage stETH market pricing and its underlying collateral.

The stETH ARM quotes a price for stETH based on Lido's withdrawal queue timing, letting arbitrageurs sell stETH into its ETH liquidity at a discount. When the ARM receives stETH from users, it redeems stETH 1:1 for ETH through Lido's withdrawal queue. The delta between the discounted price and the 1:1 price accrues as yield to stETH ARM LPs.

{% hint style="info" %}
See [Risk, Controls & Redemptions](arm-risk-controls-and-redemptions.md) for details on allocate(), operator controls, active lending-market selection, pause authority, and redemption timing.
{% endhint %}

### **Lido x Origin: stETH ARM**

The stETH ARM has become a key component of onchain liquidity infrastructure on Ethereum. Supported by the [Lido Ecosystem Foundation](https://x.com/OriginProtocol/status/1974112276069204333), it helps reinforce the stETH peg while earning sustainable yield through arbitrage and lending.

By providing liquidity to the stETH ARM, the Lido Ecosystem Foundation achieves two goals: it earns compelling yield for its treasury while supporting a tight stETH:ETH peg.

### Pricing Mechanics&#x20;

The price at which the stETH ARM bids on stETH is determined by the length of Lido's withdrawal queue and Morpho lending market rates. When withdrawal times are short, typically 1–2 days, the ARM will acquire stETH from AMMs at discounts as small as <1 basis point, provided the resulting yield exceeds Morpho WETH lending rates.&#x20;

Longer withdrawal queues result in larger expected discounts, reflecting the opportunity cost of capital tied up in the redemption process. The ARM's bid range is set manually based on prevailing market conditions and liquidity constraints. Within that range, ARM pricing is automated to remain consistently competitive across DEX aggregators, allowing the ARM to capture arbitrage volume efficiently while maintaining human oversight over acceptable discount thresholds.

### Rebalancing

The stETH ARM uses pricing to determine when it is attractive to acquire discounted stETH and redeem through Lido. Separately, idle WETH can be rebalanced between the ARM Vault and Morpho to maintain the configured liquidity buffer.

The allocate() function is permissionless and rule-based. It only moves idle WETH between the ARM and Morpho around the configured buffer; it does not independently decide to enter Lido redemption exposure.

### **Lending Market Integrations**

The stETH ARM increases its capital efficiency with lending market integrations. In addition to earning yield from arbitraging stETH, the stETH ARM routes its idle ETH liquidity to Morpho's lending markets to earn additional yield, unlocking additional upside for depositors during low-volatility periods.

WETH from the stETH ARM is sent to the [Morpho WETH ARM Vault](https://app.morpho.org/ethereum/vault/0x3Dfe70B05657949A5dB340754aD664810ac63b21/weth-arm-vault) to earn yield when arbitrage opportunities are not present. The vault lends to top ETH-denominated markets on Morpho, with the majority of WETH being used across wrapped stETH and wrapped eETH Morpho markets.

The current lending allocation is governed by the ARM liquidity buffer rather than by a standalone Morpho cap. With a 5% Buffer, up to roughly 95% of available idle WETH can be allocated to Morpho. Live allocation can be viewed in the Origin Analytics [Vault Assets table.](https://analytics.originprotocol.com/arm/1:ARM-WETH-stETH)

### **Flow of Funds**

1. LP deposits ETH into the stETH ARM vault on the [Origin dapp](https://app.originprotocol.com/#/arm/1:ARM-WETH-stETH)
2. ETH deposited in the vault is split between:
   * Vault buffer (used to arbitrage stETH pricing)
   * Morpho (anything beyond the required vault liquidity goes here to earn lending market yield)
3. ETH in the vault buffer is used by the ARM to acquire discounted stETH
4. stETH is redeemed 1:1 for ETH via Lido's withdrawal queue
5. \[Back to Step 2] Resulting ETH is split between the vault buffer and the lending market

### Vault Withdrawals&#x20;

Withdrawals from the stETH ARM are processed at NAV through a two-step withdrawal flow. LPs submit a withdrawal request and can claim once the request becomes claimable.

If sufficient WETH liquidity is available, claims may be available after the 10-minute minimum delay. If liquidity is constrained, claim timing depends on when liquidity returns to the ARM. This may come from Morpho withdrawals, completed Lido withdrawal claims, new deposits, or swap inflows.

There is no hard maximum claim latency. In Lido-heavy states, exits may depend on the Lido withdrawal queue. In Morpho-heavy states, exits may depend on available liquidity in the lending market. Large withdrawals are typically processed within 24 hours of the withdrawal request.&#x20;

### **DEX Aggregator Integrations**

The stETH ARM captures volume from DEX aggregators by offering the best rates for stETH swaps. The stETH ARM is integrated leading DEX aggregators including 1inch and CoWSwap.

### **LP Token**

The stETH ARM vault LP token is: ARM-WETH-stETH. Users who deposit into the stETH ARM's ETH Vault receive ARM-WETH-stETH, representing their share of the vault. These tokens can now be used throughout DeFi, starting with Pendle.

