# Core Concepts

Origin's three yield token products ([OETH](../../protocol/oeth/), [Super OETH](../../protocol/super-oeth/), and [OUSD](../../protocol/ousd/)) share most of the same battle-tested code. While each has its own characteristics and use cases, the same overall user experience applies across the product suite.

* **Fully collateralized at all times** - Every token in circulation can be redeemed permissionlessly for the underlying collateral, which negates any risk of a death spiral seen with algorithmic token implementations.
* **Rebasing (up only) ERC-20 compliant** - The standard version of each token features an increasing supply, which causes users' balances to grow in their wallets every day without any need to claim yield or actively stake the token. Learn more in [elastic-supply.md](elastic-supply.md "mention") and [rebasing-and-smart-contracts.md](rebasing-and-smart-contracts.md "mention").
* **Optional wrapped with ERC-4626** - For greater composability and an alternate user experience, each token can be wrapped, which results in a token version that grows in _value_ rather than _supply_. Learn more in [wrapping.md](wrapping.md "mention").
* **Ethereum first** - The security of each token relies on the integrity of the leading Layer 1 blockchain. OETH, in its wrapped form, has been bridged to Arbitrum using Chainlink's CCIP and is the core building block of Super OETH on Base. OUSD currently exists only on Ethereum Mainnet. Due to the unique yield generating characteristics of these tokens, it's best to read [bridging.md](bridging.md "mention") before transferring to any other chain.

