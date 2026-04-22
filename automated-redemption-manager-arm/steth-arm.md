# stETH ARM

## stETH ARM: Introduction

Origin’s stETH ARM offers LPs a low-risk strategy to earn passive yield on their ETH. The ARM (Automated Redemption Manager) consists of an ETH vault that is used to arbitrage stETH market pricing and its underlying collateral.

The stETH ARM uses its ETH liquidity to purchase stETH from the market at a discount and then redeems it 1:1 for ETH using Lido's withdrawal queue. The delta between the discounted price and the 1:1 price accrues as yield to stETH ARM LPs.

### **Lido x Origin: stETH ARM**

The stETH ARM has become a key component of onchain liquidity infrastructure on Ethereum. Supported by the [Lido Ecosystem Foundation](https://x.com/OriginProtocol/status/1974112276069204333), it helps reinforce the stETH peg while earning sustainable yield through arbitrage and lending.

By providing liquidity to the stETH ARM, the Lido Ecosystem Foundation achieves two goals: it earns compelling yield for its treasury while supporting a tight stETH:ETH peg.

### **Lending Market Integrations**

The stETH ARM increases its capital efficiency with lending market integrations. In addition to earning yield from arbitraging stETH redemptions, the stETH ARM routes its idle ETH liquidity to Morpho's lending markets to earn additional yield, unlocking additional upside for depositors even during low-volatility periods.

WETH from the stETH ARM is sent to the [Morpho WETH ARM Vault](https://app.morpho.org/ethereum/vault/0x3Dfe70B05657949A5dB340754aD664810ac63b21/weth-arm-vault) to earn yield when arbitrage opportunities are not present. The vault lends to top ETH-denominated markets on Morpho, with the majority of WETH being used across wrapped stETH and wrapped eETH Morpho markets.

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

### Performance Fee

Origin charges a 20% performance fee on yield generated on the stETH ARM. This fee is deducted from gross yield before distributions are made to depositors; it does not apply to principal. All fees collected are directed entirely to OGN buybacks, which flow to xOGN stakers, creating a direct link between protocol revenue and token holder value. The APYs displayed on Origin's analytics dashboard and third-party tracking platforms reflect net returns after this fee has been applied, so the figures represent what depositors actually earn.

