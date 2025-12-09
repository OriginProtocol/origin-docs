# stETH ARM

## stETH ARM: Introduction

Origin’s stETH ARM offers LPs a low-risk strategy to earn passive yield on their ETH. The ARM (Automated Redemption Manager) consists of an ETH vault that is used to arbitrage stETH market pricing and its underlying collateral.

The stETH ARM uses its ETH liquidity to purchase stETH from the market at a discount and then redeems it 1:1 for ETH using Lido's withdrawal queue. The delta between the discounted price and the 1:1 price accrues as yield to stETH ARM LPs.

### **Lido x Origin: stETH ARM**

The stETH ARM has become a key component of onchain liquidity infrastructure on Ethereum. Supported by the [Lido Ecosystem Foundation](https://x.com/OriginProtocol/status/1974112276069204333), it helps reinforce the stETH peg while earning sustainable yield through arbitrage and lending.

By providing liquidity to the stETH ARM, the Lido Ecosystem Foundation achieves two goals: it earns compelling yield for its treasury while supporting a tight stETH:ETH peg.

### **Lending Market Integrations**

The stETH ARM increases its capital efficiency with lending market integrations. In addition to earning yield from arbitraging stETH redemptions, the stETH ARM routes its idle ETH liquidity to Morpho's lending markets to earn additional yield, unlocking additional upside for depositors even during low-volatility periods.

### **Flow of Funds**

1. LP deposits ETH into the stETH ARM vault [using the Origin dapp](https://app.originprotocol.com/#/arm/146:ARM-WS-OS)
2. ETH deposited in the vault is split between:
   * Vault buffer (used to arbitrage stETH pricing)
   * Morpho (anything beyond the required vault liquidity goes here to earn lending market yield)
3. ETH in the vault buffer is used by the ARM to acquire stETH at a discount
4. stETH is redeemed 1:1 for ETH via Lido's withdrawal queue
5. \[Back to Step 2] Resulting ETH is split between the vault buffer and the lending market

### **DEX Aggregator Integrations**

The stETH ARM captures volume from DEX aggregators by offering the best rates for stETH swaps. The stETH ARM is integrated leading DEX aggregators including 1inch and CoWSwap.

### **LP Token**

The stETH ARM vault LP token is: ARM-WETH-stETH. Users who deposit into the stETH ARM's ETH Vault receive ARM-WETH-stETH, representing their share of the vault. These tokens can now be used throughout DeFi, starting with Pendle.

