# Wrapping

Wrapped versions of OETH and OUSD are available as non-rebasing alternatives that still earn yield. This makes it easier to use these tokens as building blocks in other contracts. The wrapped versions may also provide tax benefits in some jurisdictions.

![Two flavors, up only](https://cdn-images-1.medium.com/max/1600/1\*cqRG-8-64XYx9QChoMxk3g.png)

### How wrapped tokens work

When you wrap OETH, you get a fixed number of wOETH tokens in return. This number will not go up - you will have the same number of wOETH tokens tomorrow as you have today. However, the number of OETH tokens you can unwrap will increase over time. For example, if you wrap 10,000 OETH, you might receive 9,423 wOETH. If you hold for a while, you will still have 9,423 wOETH. But when you unwrap the wOETH, you receive 11,500 OETH.

Both OETH and wOETH earn at the same rate and can be transferred just like any other ERC-20 token. wOUSD was one of the first implementations of [ERC-4626](https://eips.ethereum.org/EIPS/eip-4626), which is an extension of ERC-20 that provides basic functionality for depositing and withdrawing tokens and reading balances on a tokenized vault. wOUSD was independently [audited by Solidified](https://github.com/OriginProtocol/security/blob/3dc8c1dec2f6fbf4f7d0bdf92408f79262624647/audits/Solidified%20-%20OGV,%20wOUSD,%20and%20ERC721a%20-%20May%202022.pdf) in May 2022. wOETH uses the same smart contract code and has been in production since March 2023.

### Wrapping

OETH and OUSD can be wrapped using their respective swap forms in the [Origin dapp](https://originprotocol.eth.limo).

<figure><img src="../.gitbook/assets/Screenshot 2024-05-25 at 23.19.09.png" alt=""><figcaption><p>Lossless token wrapping in the Origin dapp</p></figcaption></figure>

wOETH is also a supported swap route in [1inch](https://app.1inch.io/), which enables onboarding directly to wOETH from ETH or any other token.

### Unwrapping

Converting back to the underlying yield-bearing tokens does not require any ERC-20 approvals. There's also no minimum term or lockup period. You can use the same swap form in the [Origin dapp](https://originprotocol.eth.limo) to unwrap OETH or OUSD or use Etherscan to call the `withdraw` function if you prefer to specify the amount of [OETH](https://etherscan.io/address/0xdcee70654261af21c44c093c300ed3bb97b78192#writeProxyContract#F13) or [OUSD](https://etherscan.io/address/0xd2af830e8cbdfed6cc11bab697bb25496ed6fa62#writeProxyContract#F13) to be taken out.
