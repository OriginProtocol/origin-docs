# OS ARM

## **OS ARM: Introduction**

Origin’s Automated Redemption Manager (ARM) is also available on Sonic.

Origin’s OS ARM offers depositors a low-risk, passive yield strategy to earn yield on Sonic’s native token, S. This is Origin’s second ARM, following the successful launch of the stETH ARM vault on Ethereum, which arbitrages the stETH market pricing and its underlying collateral value. The OS ARM applies the same redemption-based strategy on Sonic, capturing yield from LST peg volatility, supporting the OS peg, and leveraging new efficiencies unique to Sonic’s architecture.

### **How it Works**

Origin’s ARMs earn yield by arbitraging yield-bearing token pricing. The OS ARM purchases OS from AMMs at a discount and redeems it 1:1 for S — generating low-risk yield in the process.

### **Lending Market Integrations**

The OS ARM increases its capital efficiency with lending market integrations. In addition to earning yield from arbitraging OS redemptions, the OS ARM routes its idle S liquidity to Silo’s lending markets to earn additional yield, unlocking additional upside for depositors even during low-volatility periods.

### **Flow of Funds**

1. LP deposits S into the OS ARM vault [using the Origin dapp](https://app.originprotocol.com/#/arm/146:ARM-WS-OS)
2. S deposited in the vault is split between:
   * Vault buffer (used to arbitrage OS pricing)
   * SILO (anything beyond the required vault liquidity goes here to earn lending market yield)
3. S in the vault buffer is used by the ARM to acquire OS at a discount
4. OS is redeemed 1:1 for S via Sonic’s 14 day unstaking process (the delta between the discounted price and the 1:1 price accrues as yield to the OS ARM)
5. \[Back to Step 2] Resulting S is split between the vault buffer and the lending market

### Rebalancing

Idle S can be routed to Silo when it is not needed for immediate ARM liquidity. Rebalancing around the configured ARM buffer is separate from redemption exposure, which is created when the ARM buys discounted OS and redeems it through Sonic’s unstaking process.

### **Redemptions**

Withdrawals from the ARM are processed on-demand when liquidity is available. However, because OS must be redeemed through Sonic’s unstaking process which is hardcoded at 14 days, large redemptions can take up to 14-15 days. In the case that the ARM receives additional user deposits, withdrawal liquidity may be available sooner.

Redemptions follow the ARM two-step request/claim flow. The 10-minute delay is the minimum claim delay when liquidity is available. For large withdrawals or liquidity-constrained periods, claim timing may depend on Sonic unstaking, Silo liquidity, new deposits, or swap inflows.

### **DEX Aggregator Integrations**

By offering the best rates for OS swaps, the ARM S Vault captures volume from DEX aggregators. The ARM S Vault is integrated with KyberSwap and OpenOcean at launch, two of the leading DEX aggregators on Sonic.

### **LP Token**

The OS ARM vault LP token is: ARM-WS-OS. Users who deposit into the OS ARM's S Vault receive ARM-WS-OS, representing their share of the vault. These tokens can now be used throughout DeFi, starting with lending and borrowing on Silo.

### Performance Fee

Origin charges a 20% performance fee on yield generated on the OS ARM. This fee is deducted from gross yield before distributions are made to depositors; it does not apply to principal. Net protocol fees are directed to OGN buybacks, which flow to xOGN stakers, creating a direct link between protocol revenue and token holder value. The APYs displayed on Origin's analytics dashboard and third-party tracking platforms reflect net returns after this fee has been applied, so the figures represent what depositors actually earn.

