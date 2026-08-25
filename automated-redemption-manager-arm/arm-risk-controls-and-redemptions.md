# ARM Risk, Controls & Redemptions

This page covers capital allocation, rebalancing mechanics, redemption exit timing, NAV calculation, access controls, and operational security topics that apply across all ARM deployments. For deployment-specific contract addresses, fee configuration, market whitelists, and audit history, see the individual ARM product pages.

### Capital Allocation and Lending Buffer

ARM Vault capital is split between immediate vault liquidity, redemption and arbitrage exposure, and external lending markets. On Ethereum ARM deployments, idle WETH can be routed to the Morpho WETH ARM Vault when arbitrage opportunities are not present. The sUSDe ARM routes idle USDe to Aave V3 under the same buffer-governed model.

Both lending destinations carry smart contract and utilization risk: withdrawal timing can be affected during periods of high borrowing demand in the active market. The Morpho WETH ARM Vault allocates to highly liquid, ETH-based markets that have been externally audited and vetted by the Origin Protocol team; Aave V3 has a long audit history and secures billions of dollars in capital across its markets.

There is no standalone hard cap on the Morpho lending share of the book. Instead, lending allocation is governed by the configured ARM liquidity buffer. The amount currently allocated to lending markets can be monitored on the [Origin Analytics dashboard.](https://analytics.originprotocol.com/arm/1:ARM-WETH-stETH)

### Rebalancing and allocate()

allocate() is a permissionless, rule-based rebalance function. It rebalances idle assets between the ARM Vault and the active lending market to maintain the configured liquidity buffer.

allocate() does not itself decide whether the ARM should enter redemption exposure. Redemption exposure is created by swap flow and ARM pricing: when the ARM purchases discounted stETH, eETH, or sUSDe on DEXs, those assets are later redeemed through the underlying protocol's withdrawal process. Pricing bands and withdrawal batching are controlled by the operator.

* allocate() is permissionless, any address can call it.
* It only moves idle liquidity between the ARM Vault and the active lending market.
* It does not control the ARM's entry into redemption exposure.

### Redemptions and Exit Timing

ARM redemptions use a two-step flow. LPs first submit a redemption request, then claim once the request becomes claimable.

If sufficient vault liquidity is available, a redemption may be claimable after the 10-minute minimum delay. If liquidity is unavailable, the request remains pending until liquidity returns.

Exit timing depends on the state of the book:

* **Redemption-heavy state:** Exits may depend on the underlying protocol's withdrawal queue, such as Lido, Ether.fi, Ethena, or the applicable withdrawal mechanics for that protocol.
* **Lending-heavy state:** Exits may depend on whether the active lending market has sufficient available liquidity to withdraw.
* New deposits and swap inflows can restore liquidity independently and may shorten exit times.

There is no hard maximum claim latency. LPs should monitor available liquidity, withdrawal queue depth, and lending-market exposure before requesting large redemptions. On average, 95% of withdrawals are processed within 24 hours of the withdrawal request.

### ARM Pricing and Oracle Risk

The operator sets the ARM's bid price for redeemable assets based on observed withdrawal queue depth, lending market rates, and market price data. There is no external price oracle feeding ARM's pricing function, which removes oracle manipulation risk from the ARM's core pricing mechanism.

Buy and sell prices must remain within a narrow range of an owner-set crossPrice, which bounds how far operator pricing can drift from fair value and acts as a guardrail for LPs.

### NAV Calculation for Redemptions

Redemption NAV is set at request time. If NAV decreases before claim, the claim amount is reduced to the lower claim-time NAV — this protects remaining LPs from losses that occur after a redemption request is queued. If NAV increases before claim, the claimant receives the higher claim-time rate.

### Role Model: Owner, Operator, and Permissionless Callers

The ARM is not fully dependent on a single keeper for all operations. Core buffer rebalancing through allocate() is permissionless. If the operator is offline, existing pricing remains active, completed withdrawals can still be claimed, and allocate() can still be called. However, new pricing updates and new withdrawal batching require operator or owner intervention.

<table><thead><tr><th width="178.1337890625">Role</th><th>Capability</th></tr></thead><tbody><tr><td>Permissionless Callers</td><td>Can call allocate() to rebalance idle assets are the ARM Vault liquidity buffer.</td></tr><tr><td>Operator</td><td>Can update ARM prices, switch the active lending market within owner-approved whitelist, adjust the ARM buffer, and initiate and operate withdrawal batching.</td></tr><tr><td>Owner</td><td>Controls upgrades, fee configuration, market whitelist changes, operator assignment, and other admin actions.</td></tr></tbody></table>

### Active Lending Market Controls

The operator can switch the active lending market only to a market already present in the supportedMarkets whitelist. The operator cannot point the ARM to an arbitrary adapter.

Only the Owner can add or remove supported markets. Switching markets also requires the ARM to exit the previous market first, so high utilization or insufficient liquidity in the previous market can delay a switch.

### Operational Key Security

Operational signing uses hardened key management and transaction controls. Additional operational-security detail can be provided through the diligence process where appropriate.
