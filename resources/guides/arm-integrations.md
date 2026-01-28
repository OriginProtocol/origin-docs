# ARM Integrations

### Integrating Origin’s Automated Redemption Manager (ARM)

This guide covers protocol-level integrations for Origin’s ARM vaults. It applies to all ARM deployments, including `ARM-WETH-stETH`, `ARM-USDe-sUSDe`, `ARM-WETH-eETH`, and `ARM-WS-OS`. All ARM vaults share the same integration behavior.

### Vault Behavior

ARM vaults issue a non-rebasing ERC-20 share token representing a proportional claim on vault assets. Share balances do not change over time; yield accrues through changes in the share exchange rate rather than rebasing.

ARM vaults expose a vault-like interface for deposits, redemptions, and share valuation. While similar to ERC-4626, the interface differs to support asynchronous withdrawals.

### Entry and Exit

Deposits are synchronous and return ARM shares immediately. Integrators may optionally call `previewDeposit` prior to depositing to estimate shares received.

Redemptions follow a two-step flow. Users first submit a redemption request using `requestRedeem`. If sufficient liquidity is available in the vault, the redemption may be claimable after a 10 minute delay. Otherwise, the request remains pending until liquidity is returned, at which point `claimRedeem` can be called to complete the exit. Integrations should assume that redemptions may not be instantly claimable and handle pending claims accordingly.

When instant liquidity is unavailable, withdrawals follow the underlying asset’s withdrawal mechanics, such as the stETH withdrawal queue for ARM-WETH-stETH. For select ARM deployments, including the stETH ARM, there is onchain liquidity available via AMMs.

### Share Valuation

ARM share value should be derived using the vault’s onchain conversion functions, such as `convertToAssets`, rather than AMM spot prices. This provides the canonical share-to-asset exchange rate for accounting and risk calculations.

For integrations that require a USD price, protocols typically combine the share exchange rate with their preferred oracle for the underlying asset. ARM shares should not be treated as 1:1 with ETH or other base assets.

### Pricing and Oracles

ARM vaults do not rely on AMM pricing for valuation. Integrations should avoid using pool spot prices as an oracle due to potential liquidity constraints and price dislocations.

When oracle pricing is required, protocols should compose pricing from the onchain share exchange rate and an external oracle for the underlying asset. Oracle provider selection and risk parameters are left to the integrating protocol.

### Integration Considerations

Lending protocols should account for redemption latency when modeling collateral risk and liquidation behavior. Vault aggregators should compute NAV using share conversion functions and surface pending redemptions clearly to users. AMMs, when used, should be treated as optional liquidity venues rather than authoritative pricing sources.

### Failure Modes and Edge Cases

Calls to `claimRedeem` may revert until a redemption request becomes claimable. Integrations should handle this behavior gracefully. Preview functions are estimations and may be affected by rounding. Integrators should avoid assumptions of guaranteed immediate settlement.
