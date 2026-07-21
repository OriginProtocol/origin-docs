# eETH ARM

## **eETH ARM: Introduction**

Origin’s Automated Redemption Manager (ARM) supports instant redemptions for Ether.fi’s eETH.

The eETH ARM applies the same redemption-based strategy pioneered by the stETH ARM. It arbitrages the pricing of Ether.fi’s liquid staking token, eETH, against its underlying collateral value, capturing yield from peg volatility while improving instant exit liquidity on eETH. This design gives depositors a low-risk, passive way to earn ETH yield  without needing to manually manage their position or monitor spreads.

### **How it Works**

The eETH ARM earns yield by quoting a price for eETH based on Ether.fi's withdrawal timing, letting users sell discounted eETH into its liquidity before the ARM redeems it 1:1 for ETH through Ether.fi's withdrawal process. The spread between the market price and the redemption value becomes yield for eETH ARM depositors. This approach consistently monetizes short-term peg deviations while helping stabilize eETH's onchain market pricing.

### **Lending Market Integrations**

To increase capital efficiency, the eETH ARM routes unused WETH to Morpho to earn lending yields when arbitrage opportunities are not present. WETH from the eETH ARM Vault is sent to the [Morpho WETH ARM Vault](https://app.morpho.org/ethereum/vault/0x3Dfe70B05657949A5dB340754aD664810ac63b21/weth-arm-vault) to earn yield. The vault lends to top ETH-denominated markets on Morpho, with the majority of WETH being used across wrapped stETH and wrapped eETH Morpho markets.

### **Flow of Funds**

1. LP deposits ETH into the eETH ARM vault [using the Origin dapp](https://app.originprotocol.com/#/arm/)
2. ETH deposited in the vault is split between:
   * Vault buffer (used to arbitrage eETH market pricing)
   * Morpho (anything beyond the required vault liquidity goes here to earn lending market yield)
3. ETH in the vault buffer is used by the ARM to acquire eETH at a discount
4. eETH is redeemed 1:1 for ETH via Ether.fi’s withdrawal queue (the delta between the discounted price and the 1:1 price accrues as yield to the eETH ARM)
5. \[Back to Step 2] Resulting ETH is split between the vault buffer and Morpho

### Rebalancing

allocate() is permissionless and rebalances idle WETH between the ARM and Morpho around the configured ARM buffer. It does not independently choose eETH redemption exposure; that exposure is driven by ARM pricing, swap flow, and withdrawal batching.

### **Vault Withdrawals**

Withdrawals from the ARM are processed on-demand when liquidity is available. However, because eETH must be redeemed through Ether.fi’s unstaking process which is asynchronous, large withdrawals can take up to 7-15 days. In the case that the ARM receives additional user deposits, withdrawal liquidity may be available sooner.

Withdrawals follow the ARM two-step flow: request first, then claim once liquidity is available. The 10-minute delay is the minimum claim delay, not a guarantee that every redemption will be claimable after 10 minutes.

If WETH liquidity is available in the ARM, exits can be faster. If liquidity is constrained, claim timing may depend on Ether.fi withdrawal processing, Morpho liquidity, new deposits, or swap inflows.

### **DEX Aggregator Integrations**

By offering the best rates for eETH swaps, the eETH ARM captures volume from DEX aggregators. Aggregators that the eETH ARM Vault is integrated with include: KyberSwap, OpenOcean, 1inch, Velora, Cowswap, and Fly.

### **LP Token**

The eETH ARM vault LP token is: ARM-WETH-eETH. Users who deposit into the eETH ARM's ETH Vault receive ARM-WETH-eETH, representing their share of the vault. These tokens will soon expand throughout DeFi for lending, borrowing, and trading.

### Performance Fee

Origin charges a 20% performance fee on yield generated on the eETH ARM. This fee is deducted from gross yield before distributions are made to depositors; it does not apply to principal. Net protocol fees are directed to OGN buybacks, which flow to xOGN stakers, creating a direct link between protocol revenue and token holder value. The APYs displayed on Origin's analytics dashboard and third-party tracking platforms reflect net returns after this fee has been applied, so the figures represent what depositors actually earn.
