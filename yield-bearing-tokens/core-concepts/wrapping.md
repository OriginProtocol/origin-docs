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

# Wrapping

Wrapped versions of OETH, OUSD, Super OETH, and OS are available as non-rebasing alternatives that still earn yield. This makes it easier to use these tokens as building blocks in other contracts. The wrapped versions may also provide tax benefits in some jurisdictions.

{% hint style="info" %}
All wrapped versions of Origin’s yield-bearing tokens are ERC-4626 compliant. These tokens are protected from donation attacks and are ideal for supplying to money markets such Morpho and Compound. See our [wrapped token audit](https://github.com/OriginProtocol/security/blob/master/audits/OpenZeppelin%20-%20Origin%20WOETH%20and%20Vault%20Update%20-%20April%202025.pdf) here.
{% endhint %}

![Two flavors, up only](https://cdn-images-1.medium.com/max/1600/1*cqRG-8-64XYx9QChoMxk3g.png)

### How Wrapped Tokens Work

When you wrap an OToken, you get a fixed number of wrapped tokens in return. This number will not go up. If you wrap OETH, for example, you will hold the same number of wOETH tokens in the future as you have today. However, the number of OETH tokens you can unwrap will increase over time. For example, if you wrap 10,000 OETH, you might receive 9,423 wOETH. If you hold for a while, you will still have 9,423 wOETH. But when you unwrap the wOETH, you receive 11,000 OETH.

Both OETH and wOETH earn at the same rate and can be transferred just like any other ERC-20 token. wOUSD was one of the first implementations of [ERC-4626](https://eips.ethereum.org/EIPS/eip-4626), which is an extension of ERC-20 that provides basic functionality for depositing and withdrawing tokens and reading balances on a tokenized vault. wOUSD was independently [audited by Solidified](https://github.com/OriginProtocol/security/blob/3dc8c1dec2f6fbf4f7d0bdf92408f79262624647/audits/Solidified%20-%20OGV,%20wOUSD,%20and%20ERC721a%20-%20May%202022.pdf) in May 2022.

{% hint style="info" %}
wOUSD, wOETH, wOS, and wsuperOETHb use the same smart contract code.
{% endhint %}

### Wrapping

OS, Super OETH, OETH and OUSD can be wrapped using their respective swap forms in the [Origin dapp.](https://app.originprotocol.com/)

<figure><img src="../../.gitbook/assets/Screenshot 2024-05-25 at 23.19.09.png" alt=""><figcaption><p>Lossless token wrapping in the Origin dapp</p></figcaption></figure>

wOETH is also a supported swap route in [1inch](https://app.1inch.io/), which enables onboarding directly to wOETH from ETH or any other token.

### Unwrapping

Converting back to the underlying yield-bearing tokens does not require any ERC-20 approvals. There's also no minimum term or lockup period. You can use the same swap form in the [Origin dapp](https://app.originprotocol.com/) to unwrap any of the OTokens or to call contract's withdraw function.
