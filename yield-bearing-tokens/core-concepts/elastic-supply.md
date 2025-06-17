---
description: Up-Only Supply. Stable Price.
layout:
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
---

# Elastic Supply

OTokens (OUSD, OETH, Super OETH, and OS) work differently than most tokens. Instead of the price increasing as the value of the assets under management increases (as with Compound cTokens or Yearn yTokens), the value of 1 OUSD remains constant at approximately $1. Similarly, the value of 1 OETH is worth approximately 1 ETH. The contracts constantly adjust the monetary supply to automatically update the balance in every token holder’s wallet to reflect the yield that has been earned by the protocol.

{% hint style="info" %}
Think of it as interest accruing in your bank account. The unit of account and value for the US dollar doesn’t change. You just get more US dollars over time as you earn interest.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

This mechanism was inspired by the novel approach taken by [Ampleforth](https://www.ampleforth.org/), but there are some key differences that are worth highlighting:

1. OTokens can be redeemed for their underlying collateral at any time. Given the ease of minting and redeeming them, we can count on arbitrageurs to ensure the peg is maintained.
2. OToken rebasing is up-only. The protocol will only increase the supply to match the realized gains earned by the underlying strategies. Your principal is protected as long as nothing goes wrong with the underlying strategies. Your balance will never decrease, but the value should drop if there's a failure in the underlying systems (eg. USDC depegs again)
3. Unlike Ampleforth, which only rebases once per day, the monetary supply of OTokens are constantly being updated in real-time as yield is generated. Rebases are triggered regularly as users interact with the OToken contracts. Chainlink Keepers ensure at least one rebase occurs every day.

**Manually triggering a rebase**

Anyone can trigger a rebase of an OToken at any time by calling the **rebase** function on the vault. On Etherscan you can do this by connecting a web3 wallet.
