---
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# Core Concepts

Origin's four yield-bearing token products ([OETH](https://docs.originprotocol.com/yield-bearing-tokens/oeth), [Super OETH](https://docs.originprotocol.com/yield-bearing-tokens/super-oeth), [OS](https://docs.originprotocol.com/yield-bearing-tokens/os), and [OUSD](https://docs.originprotocol.com/yield-bearing-tokens/ousd)) share most of the same battle-tested code. While each has its own characteristics and use cases, the same overall user experience applies across the product suite:

* **Fully collateralized** - Every token in circulation can be redeemed permissionlessly for its underlying collateral, which negates any risk of a death spiral seen with algorithmic token implementations.
* **Rebasing ERC-20 compliant** - The standard version of each token features an increasing supply, which causes users' balances to grow in their wallets every day as yield is earned. This “up only” rebasing eliminates the need to claim yield or actively stake tokens for yield. Learn more in  [Rebasing & Smart Contracts](https://docs.originprotocol.com/yield-bearing-tokens/core-concepts/rebasing-and-smart-contracts).
* **Wrapped tokens via ERC-4626** - For greater composability and an alternate user experience, each token can be wrapped, which results in a token version that grows in _value_ rather than _supply_. Learn more in [Wrapping](https://docs.originprotocol.com/yield-bearing-tokens/core-concepts/wrapping).
* **Integrated with protocol-owned liquidity** - Peg stability and yield are optimized in each case by pairing collateral with a tightly controlled token issuance strategy. Learn more in [AMO](https://docs.originprotocol.com/yield-bearing-tokens/core-concepts/amo).

