---
description: Protecting OUSD from market volatility
---

# Pricing and Peg Management

Origin’s yield-bearing tokens are designed to closely track their underlying assets. Each token is fully backed by high quality collateral and priced using a combination of protocol rules and external oracles.

### Rebasing and 1:1 Accounting

Origin’s yield-bearing tokens use a simple accounting model that treats one unit of underlying collateral as one unit of the yield-bearing token. This means that 1 OUSD is worth exactly 1 USDC, while 1 OETH is worth exactly 1 ETH upon redemption.

Rebasing increases balances based on strategy performance. Holder balances move upward as yield is earned and more collateral is added to the backing supply. There is no scenario where a negative rebase may occur. Since wrapped token supply doesn’t increase as yield is earned, price is calculated using the total assets divided by the total supply of the wrapped token.

This approach is consistent with many ERC-4626 vault integrations, which commonly hardcode their rebasing counterparts at 1:1 with the base asset (for example, treating 1 OUSD as 1 USDC or 1 OETH/Super OETH as 1 ETH) at the accounting layer, even when the underlying trades slightly off its target.

### Minting, Redemption, and Oracle Pricing

To mint and redeem the correct amounts of Origin’s yield-bearing tokens, the protocol must value the collateral entering and exiting the system. Pricing is sourced directly from the token’s underlying value, ensuring 1:1 mint and redeems for all of Origin’s yield-bearing tokens.

Strict caps on mint and redeem prices ensure that mispriced oracle inputs cannot cause the protocol to overpay for collateral or under-redeem it. In scenarios where collateral is acquired at a discount (for example, during periods of minor depegs), the difference accrues to token holders as additional yield.

### ARM Pricing

The ARM uses a number of different pricing strategies. ARM pricing is relative to DEX aggregators like 1Inch or Kyber. Pricing parameters control how close the price is relative to the DEX price. For example, the Lido ARM can be set to buy stETH at 0.1 basis points better than Kyber and sell stETH at 0.8 basis points more than what it bought it. The buy and sell prices can be held in a range and prices can only be updated if the relative price moves more than a set tolerance amount.

Pricing can also be done relative to the estimated withdrawal time and lending platform rate. For example, the OS ARM pricing estimates the OS Vault’s withdrawal time and uses lending market rates to calculate a comparable discount for the ARM to buy OS.

Repricing is triggered off-chain if there is a large swap on the ARM or a related DEX pool. If the recalculated price is more than the tolerance level, a transaction is broadcast to update the onchain price. There are also regular reprice checks.

