# AMO

OETH, Super OETH, OS, and OUSD all utilize Automated Market Operations (AMO). The AMO helps to maintain the peg, increases capital efficiency, and maximizes yield for holders. The AMO is allowed to enact monetary policy within a closed system so long as it does not negatively impact the peg. The protocol remains 100% collateralized at all times even as the money supply programmatically expands and contracts in response to market conditions.

{% hint style="info" %}
The AMO helps to maintain the peg, increases capital efficiency, and maximizes yield for OETH, Super OETH, OS, and OUSD holders.&#x20;
{% endhint %}

**How the AMO Works**

AMMs count the number of coins on each side of a pool to determine the current price. In order to maintain the peg, both sides of a pool must remain balanced.&#x20;

Therefore, when the protocol deposits funds into a pool, it deploys liquidity to both sides of the pool. In the case of OETH, it deploys OETH on one side and ETH on the other. For OS, it deploys OS on one side and S on the other, etc. This ensures that after deploying liquidity, the balance of the pool doesn't change. Note: there are additional constraints in place that ensure the exchange rate in the pool does not deviate beyond a narrow threshold (0.0001% in the case of Super OETH).&#x20;

When the pools get unbalanced, the AMO can add or remove liquidity from one side of the pool to bring it back into balance. If the OETH/ETH pool contains more ETH than OETH, for example, the AMO deploys extra OETH to bring the pool back into balance. This approach of providing up to double the liquidity to the pool allows the protocol to earn up to twice as many rewards using the same amount of capital. &#x20;

This feature can also work in reverse, with the AMO removing extra OUSD, OETH, OS or Super OETH from the pool when necessary. This ensures peg stability with high capital efficiency.

#### Protocol Owned Liquidity

Remaining 100% collateralized is an important bedrock component of the protocol. It may sound counterintuitive that the protocol can remain fully collateralized even while deploying unbacked tokens into the pool. But those unbacked tokens will never enter circulation without being fully collateralized.&#x20;

{% hint style="info" %}
The OUSD, OETH, OS, and Super OETH held by the AMO never enter circulation without being fully collateralized.&#x20;
{% endhint %}

Let's look at an example to understand how this is possible:

* 1,000 OETH/ETH has been deployed into the Curve pool by the AMO. (This means the protocol owns 500 ETH and 500 unbacked OETH.)
* A user comes along and swaps 100 ETH for 99.9 OETH. (They receive slightly fewer units of OETH because of trading fees and slippage.)&#x20;
* At the end of this transaction, the user is holding 99.9 OETH and the protocol is holding 600.1 ETH and 400 unbacked OETH. (The extra .1 ETH is owned by the the protocol) and is distributed to holders as extra profit.)

{% hint style="info" %}
Since the user must transfer their ETH to the Curve pool in order to withdraw OETH, the previously unbacked OETH immediately becomes backed as part of the transaction. You can think of it as the vault pre-minting some OETH for Curve to sell on its behalf with those tokens become 100% backed the minute they enter circulation.&#x20;
{% endhint %}

Ultimately, OUSD, OETH, Super OETH, and OS can still be redeemed at any time for the underlying collateral on a 1:1 basis.&#x20;

This model has been extensively tested and demonstrated to work safely at scale. In addition, the Origin team has also completed extensive testing in forked Mainnet node environment simulating how flash loans could mint large amounts, deploy liquidity and then redeem it, manipulating the AMO at various stages of that procedure. No vulnerabilities have been found. For safety, funds are never directly deployed or withdrawn from the AMO as a result of a mint or redeem. Like the rest of the code, the AMO has been thoroughly audited by OpenZeppelin and others.
