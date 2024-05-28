# Redemption

As a permissionless protocol with no gatekeepers, OETH supports redemption by anyone at any time. While there are four different ways to exit OETH, users can go through the Origin dapp to get the best outcome without needing to consider every option.

1. **Instant vault redemption** - The OETH vault's `redeem` function takes any amount of OETH and burns it in exchange for WETH at a rate of 1:0.999. This fee of 0.1% protects the protocol from any malicious attacks that could theoretically result from rounding errors. While this redemption feature limits the downside for anyone holding OETH, it is expected to be deprecated with the introduction of async withdrawals and instant 1:1 ARM swaps.
2. **DEX swap** - The OETH/ETH Curve pool features deep exit liquidity allowing anyone to swap OETH for ETH at the current spot price. This rate fluctuates based on market demand but is often arbitraged back to near 1:1 anytime it falls due to a large sale.
3. **Async withdrawal** - Coming _very_ soon™️
4. **Instant 1:1 ARM swap** - Coming _very_ soon™️

Redemption is a critical feature for any LST and is paramount for OETH to remain the optimal building block for DeFi protocols. Allowing users to confidently hold OETH knowing they can exit at virtually 1:1 for ETH anytime will always be OETH's top priority.
