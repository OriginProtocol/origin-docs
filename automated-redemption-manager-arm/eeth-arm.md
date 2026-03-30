# eETH ARM

## **eETH ARM: Introduction**

Origin’s Automated Redemption Manager (ARM) supports instant redemptions for [Ether.fi](http://ether.fi)’s eETH.

The eETH ARM applies the same redemption-based strategy pioneered by the stETH ARM. It arbitrages the pricing of [Ether.fi](http://ether.fi/)’s liquid staking token, eETH, against its underlying collateral value, capturing yield from peg volatility while improving instant exit liquidity on eETH. This design gives depositors a low-risk, passive way to earn yield in ETH without needing to manually manage their position or monitor spreads.

### **How it Works**

The eETH ARM earns yield by buying discounted eETH on AMMs and redeeming it 1:1 for ETH through [Ether.fi](http://ether.fi)’s withdrawal process. The spread between the market price and the redemption value becomes yield for eETH ARM depositors. This approach consistently monetizes short-term peg deviations while helping stabilize eETH’s onchain market pricing.

### **Lending Market Integrations**

To increase capital efficiency, the eETH ARM routes unused WETH to Morpho to earn lending yields when arbitrage opportunities are not present. WETH from the eETH ARM Vault is sent to the [Morpho WETH ARM Vault](https://app.morpho.org/ethereum/vault/0x3Dfe70B05657949A5dB340754aD664810ac63b21/weth-arm-vault) to earn yield. The vault lends to top ETH-denominated markets on Morpho, with the majority of WETH being used across wrapped stETH and wrapped eETH Morpho markets.

### **Flow of Funds**

1. LP deposits ETH into the eETH ARM vault [using the Origin dapp](https://app.originprotocol.com/#/arm/)
2. ETH deposited in the vault is split between:
   * Vault buffer (used to arbitrage eETH market pricing)
   * Morpho (anything beyond the required vault liquidity goes here to earn lending market yield)
3. ETH in the vault buffer is used by the ARM to acquire eETH at a discount
4. eETH is redeemed 1:1 for ETH via [Ether.fi](http://ether.fi)’s withdrawal queue (the delta between the discounted price and the 1:1 price accrues as yield to the eETH ARM)
5. \[Back to Step 2] Resulting ETH is split between the vault buffer and Morpho

### **Redemptions**

Withdrawals from the ARM are processed on-demand when liquidity is available. However, because eETH must be redeemed through [Ether.fi](http://ether.fi)’s unstaking process which is is asynchronous, redemptions for large withdrawals can take 7-15 days. In the case that the ARM receives additional user deposits, withdrawal liquidity may be available sooner.

### **DEX Aggregator Integrations**

By offering the best rates for eETH swaps, the eETH ARM captures volume from DEX aggregators. Aggregators that the eETH ARM Vault is integrated with include: KyberSwap, OpenOcean, 1inch, Velora, Cowswap, and Fly.

### **LP Token**

The eETH ARM vault LP token is: ARM-WETH-eETH. Users who deposit into the eETH ARM's ETH Vault receive ARM-WETH-eETH, representing their share of the vault. These tokens will soon expand throughout DeFi for lending, borrowing, and trading.
