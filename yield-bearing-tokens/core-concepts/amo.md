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

# AMO

OETH, Super OETH, OS, and OUSD all utilize Automated Market Operations (AMOs). The AMO helps to maintain the peg, increases capital efficiency, and maximizes yield for holders. The AMO is allowed to enact monetary policy within a closed system so long as it does not negatively impact the peg. The protocol remains 100% collateralized at all times even as the money supply programmatically expands and contracts within liquidity pools in response to market conditions.

{% hint style="info" %}
The AMO helps to maintain the peg, increases capital efficiency, and deploys deep liquidity for OETH, Super OETH, OS, and OUSD holders.
{% endhint %}

### How the AMO Works

AMMs count the number of coins on each side of a pool to determine the current price. In order to maintain the peg, both sides of a pool must remain balanced.

Therefore, when the protocol deposits funds into a pool, it deploys liquidity to both sides of the pool. In the case of OETH, it deploys OETH on one side and WETH on the other. For OUSD, it deploys OUSD on one side and USDC on the other, etc. This ensures that after deploying liquidity, the balance of the pool doesn't change.

When the pools get unbalanced, the AMO can add or remove liquidity from one side of the pool to bring it back into balance. If the OETH/ETH pool contains more ETH than OETH, for example, the AMO deploys additional OETH to bring the pool back into balance. This approach of providing up to double the liquidity to the pool allows the protocol to deploy up to twice the amount of liquidity in a given pool.

This feature can also work in reverse. The AMO can remove extra OUSD, OETH, OS or Super OETH from the pool when necessary. This ensures peg stability with high capital efficiency.

### Protocol Owned Liquidity

Remaining 100% collateralized is an important bedrock component of the protocol. It may sound counterintuitive that the protocol can remain fully collateralized even while deploying unbacked tokens into a liquidity pool. But those unbacked tokens will never enter circulation without being fully collateralized.

{% hint style="info" %}
The OUSD, OETH, OS, and Super OETH deployed by the AMO never enter circulation without being fully collateralized.&#x20;
{% endhint %}

Let's look at an example to understand how this is possible:

* Let's say 1,000 OETH/ETH has been deployed into the Curve pool by the AMO. This means the protocol owns 500 ETH and 500 unbacked OETH.
* A user comes along and swaps 100 ETH for 99.9 OETH. They receive slightly fewer units of OETH because of trading fees and slippage.
* At the end of this transaction, the user is holding 99.9 OETH and the protocol is holding 600.1 ETH and 400 unbacked OETH. The extra .1 ETH is owned by the the protocol and is distributed to holders as extra profit.

{% hint style="info" %}
Since the user must transfer their ETH to a liquidity pool in order to withdraw OETH, the previously unbacked OETH immediately becomes backed as part of the transaction. You can think of it as the vault pre-minting some OETH for Curve to sell on its behalf with those tokens becoming 100% backed as soon as they enter circulation.
{% endhint %}

Ultimately, OUSD, OETH, Super OETH, and OS can still be redeemed at any time for the underlying collateral on a 1:1 basis through direct redemptions. Origin's AMOs help traders get instant liquidity with low slippage on AMMs.

This model has been extensively tested and demonstrated to work safely at scale. The Origin team has also completed extensive testing to ensure that flash loan attacks cannot manipulate algorithmic market operations. For safety, funds are never directly deployed or withdrawn from the AMO as a result of a mint or redeem. Like the rest of the code, the AMO has been thoroughly audited by OpenZeppelin and other auditors.
