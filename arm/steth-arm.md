# stETH ARM

The stETH (ARM) offers zero-slippage swapping of stETH. You can think of an ARM as a cross between an AMM and an isolated money market as it prices assets based on current market rates and redemption queues.&#x20;

The stETH ARM offers:

* **Zero Slippage:** The ARM offers zero-slippage swaps for redeemable assets saving traders a large amount on swaps in comparison to other options on the market.
* **Market-Based Pricing**: The prices are based on the market rates at the time and the length of the redemption queue.&#x20;
* I**nstant Liquidity**: Enables 1:1 swap prices between stETH and ETH.
* **Low Fees**: The ARM is gas-optimized and provides modest trading fees.
* **Revenue Generation**: The ARM plays a pivotal role in generating protocol revenue that accrues to OGN.

The ARM is currently integrated into 1Inch and CowSwap and more integrations are on the way as the product continues to scale throughout DeFi.&#x20;

### How it works

Unlike a DEX that uses a bonding curve to price assets, ARM prices are determined by the current market rates of the underlying collateral and the length of the redemption queue.

As a concrete example, imagine that a user wants to swap out of stETH into ETH. That user can currently unstake from Lido and receive ETH 1:1, usually after several days. Or, they can swap stETH instantly for ETH on Curve or Uniswap, incurring transaction fees and slippage. For larger swaps, the slippage can be considerable, penalizing the trader for wanting to get out of a large position.

With the ARM, traders will get a far more competitive price at virtually **1:1 between stETH and ETH.** The ARM can quote these prices based on the cost of “loaning” out ETH to the trader at a very low interest rate. In practice, this almost always beats the pricing of AMMs like Uniswap, Curve, etc. Further, gas optimizations and an intentionally modest trading fee in the ARM ensure the best possible prices for traders looking for instant exit liquidity.

