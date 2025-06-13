# Core Concepts

Origin's four yield-bearing token products ([OETH](../oeth/), [Super OETH](../super-oeth/), [OS](../os/), and [OUSD](../ousd/)) share most of the same battle-tested code. While each has its own characteristics and use cases, the same overall user experience applies across the product suite:

* **Fully collateralized at all times** - Every token in circulation can be redeemed permissionlessly for the underlying collateral, which negates any risk of a death spiral seen with algorithmic token implementations.
* **Rebasing (up only) ERC-20 compliant** - The standard version of each token features an increasing supply, which causes users' balances to grow in their wallets every day without any need to claim yield or actively stake the token. Learn more in [elastic-supply.md](elastic-supply.md "mention") and [rebasing-and-smart-contracts.md](rebasing-and-smart-contracts.md "mention").
* **Optional wrapped version with ERC-4626** - For greater composability and an alternate user experience, each token can be wrapped, which results in a token version that grows in _value_ rather than _supply_. Learn more in [wrapping.md](wrapping.md "mention").
* **Integrated with protocol-owned liquidity** - Peg stability and yield are optimized in each case by pairing collateral with a tightly controlled token issuance strategy. Learn more in [amo.md](amo.md "mention").
