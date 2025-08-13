# stETH ARM

Origin’s stETH ARM offers LPs a low-risk strategy to earn passive yield on their ETH. The ARM (Automated Redemption Manager) consists of an ETH vault (ETH in, ETH out) that is used to arbitrage the stETH redemption queue.&#x20;

## **How it works**

The stETH ARM uses it's ETH liquidity to purchase stETH from the market at a discount and then redeems it 1:1 for ETH using Lido's withdrawal queue. The delta between the discounted price and the 1:1 price accrues as yield to the stETH ARM.

#### **Lending Market Integrations**

The stETH ARM increases its capital efficiency with lending market integrations. In addition to earning yield from arbitraging stETH redemptions, the stETH ARM routes its idle ETH liquidity to Morpho's lending markets to earn additional yield, unlocking additional upside for depositors even during low-volatility periods.

#### **Flow of Funds**

1. LP deposits ETH into the stETH ARM vault [using the Origin dapp](https://app.originprotocol.com/#/arm/146:ARM-WS-OS)
2. ETH deposited in the vault is split between:
   * Vault buffer (up until the required liquidity threshold is met)
   * Morpho (anything beyond the required vault liquidity goes here to earn lending market yield)
3. ETH in the vault buffer is used by the ARM to acquire stETH at a discount
4. stETH is redeemed 1:1 for ETH via Lido's withdrawal queue&#x20;
5. \[Back to Step 2] Resulting ETH is split between the vault buffer and the lending market

## **DEX Aggregator Integrations**

The stETH captures volume from DEX aggregators by offering the best rates for stETH swaps. The stETH ARM is integrated leading DEX aggregators including 1inch and CoWSwap.

## LP Token

The stETH ARM vault LP token is: ARM-WETH-stETH. Users who deposit into the stETH ARM's ETH Vault receive ARM-WETH-stETH, representing their share of the vault. These tokens can now be used throughout DeFi, starting with lending and borrowing on Morpho.

