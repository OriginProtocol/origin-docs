# sUSDe ARM

## sUSDe ARM: Introduction

Origin's sUSDe ARM is the first ARM deployment for a yield-bearing stablecoin. It earns\
yield by arbitraging the spread between sUSDe's secondary market price and its USDe\
redemption value.

The sUSDe ARM uses its USDe liquidity to sell USDe for discounted sUSDe, redeeming it for USDe through Ethena's unstaking process. The delta between the discounted purchase price and the redemption value accrues as yield to sUSDe ARM LPs. The same framework that has processed over $3B in volume across the stETH and eETH ARMs now applies to the stablecoin market.

Origin’s ARM contracts were audited by OpenZeppelin and yAudit. View the reports [here.](https://docs.originprotocol.com/security-and-risk/audits)

{% hint style="info" %}
See [Risk, Controls & Redemptions](https://docs.originprotocol.com/automated-redemption-manager-arm/arm-risk-controls-and-redemptions) for details on allocate(), operator controls, active lending-market selection, pause authority, and redemption timing.
{% endhint %}

#### Pricing Mechanics

The price at which the sUSDe ARM sells USDe for sUSDe is a function of secondary market pricing, Ethena's unstaking cooldown, and Aave V3 USDe lending market rates. The Aave V3 lending rate is the yield hurdle; the yield-implied discount from sUSDe arbitrage must surpass lending yields for the ARM to sell USDe for discounted sUSDe.

Ethena enforces a dynamic cooldown (typically 1 day) before sUSDe can be unstaked to USDe. This illiquidity during redemption is factored into the pricing mechanics: longer redemptions times require larger discounts to justify arbitrage activity.

The ARM allows DEX aggregators, MEV bots, and users to swap sUSDe for USDe at set prices.

#### Rebalancing

The pricing mechanics used by the sUSDe ARM determine when it is attractive to sell USDe for discounted sUSDe to redeem through Ethena's unstaking process. Separately, idle USDe can be rebalanced between the ARM Vault and Aave V3 to maintain the configured liquidity buffer.

The `allocate()` function is permissionless and rule-based. It only moves idle USDe between the ARM and Aave V3 around the configured buffer; it does not independently decide to enter Ethena redemption exposure.

#### Lending Market Integrations

To increase capital efficiency, the sUSDe ARM routes idle USDe to Aave V3 to earn lending yields when arbitrage opportunities are not present. USDe from the sUSDe ARM Vault is deposited into Aave V3's USDe market, where it earns yield between arbitrage cycles.

The Aave V3 lending rate establishes the ARM's yield floor. The current lending allocation is governed by the ARM liquidity buffer. Live allocation can be viewed in the Origin Analytics [Vault Assets table.](https://analytics.originprotocol.com/arm/1:ARM-sUSDe-USDe)

#### Flow of Funds

1. LP deposits USDe into the sUSDe ARM Vault on the [Origin dapp.](https://app.originprotocol.com/#/arm/1:ARM-sUSDe-USDe)
2. USDe deposited in the vault is split between:
   * Vault buffer (used to arbitrage sUSDe market pricing)
   * Aave V3 (anything beyond the required vault liquidity goes here to earn lending yield)
3. USDe in the vault buffer is used by the ARM to acquire sUSDe
4. sUSDe is redeemed for USDe via Ethena's unstaking process (dynamic 1-5 day cooldown per batch)
5. \[Back to Step 2] Resulting USDe is split between the vault buffer and Aave V3

<figure><img src="../.gitbook/assets/ARM Vault Diagram (2).png" alt=""><figcaption></figcaption></figure>

#### Vault Withdrawals&#x20;

Withdrawals from the sUSDe ARM are processed at NAV through a two-step redemption flow. LPs submit a redemption request and can claim once the request becomes claimable.

If sufficient USDe liquidity is available in the ARM, claims may be available after the\
10-minute minimum delay. If liquidity is constrained, claim timing depends on when\
liquidity returns to the ARM. This may come from Aave V3 withdrawals, completed Ethena unstaking claims, new deposits, or swap inflows.

Ethena's unstaking cooldown is a variable window with most redemptions taking 1 day per batch. In redemption-heavy states, large requests may take up to 5 days to process, with most requests being claimable within 24 hours. In Aave-heavy states, exits may depend on available liquidity in the lending market.

There is no hard maximum claim latency. LPs should monitor available vault liquidity, pending Ethena unstaking batches, and Aave V3 utilization before requesting large redemptions.

#### DEX Aggregator Integrations

The sUSDe ARM captures volume from DEX aggregators by offering the best rates for sUSDe swaps. The sUSDe ARM is integrated with leading DEX aggregators including KyberSwap, OpenOcean, Fly, and Velora.

#### LP Token

The sUSDe ARM vault LP token is: ARM-USDe-sUSDe. Users who deposit into the sUSDe ARM's USDe Vault receive ARM-USDe-sUSDe, representing their share of the vault. The token’s contract address is viewable on [Etherscan.](https://etherscan.io/token/0xCEDa2d856238aA0D12f6329de20B9115f07C366d)

The LP Token address is 0xCEDa2d856238aA0D12f6329de20B9115f07C366d

#### Performance Fee

Origin charges a 20% performance fee on yield generated from arbitrage by the sUSDe ARM. This fee is deducted from gross yield before distributions are made to depositors; it does not apply to principal. No fees are charged on lending market yields earned through Aave V3.

Net protocol fees are directed to OGN buybacks, which flow to xOGN stakers, creating a direct link between protocol revenue and token holder value. The APYs displayed on Origin's analytics dashboard and third-party tracking platforms reflect net returns after this fee has been applied, so the figures represent what depositors actually earn.
