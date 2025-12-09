# Introduction to ARM

<figure><img src="../.gitbook/assets/origin dollar (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

The Automated Redemption Manager (ARM) is Origin’s onchain liquidity engine designed to enable better exit liquidity and tighter pegs for yield-bearing assets such as stETH, eETH, and OS. The ARM continuously arbitrages between secondary market prices and the token’s underlying collateral to help tokens trade close to their underlying value.

By automating the redemption process, the ARM provides deep, efficient liquidity without relying on centralized market makers. It sources and deploys capital directly from ARM Vaults, generating sustainable yield from arbitrage activity while reinforcing price stability for yield-bearing tokens.

The result is a mechanism that strengthens liquidity across multiple protocols, improves capital efficiency, and enhances the overall stability of Ethereum’s liquid staking and yield-bearing token markets.

### **How the ARM Works**

When a liquid staking token trades below its redemption value, the ARM buys it on secondary markets and redeems it for the underlying asset directly through the protocol’s withdrawal process.

When market spreads tighten and lending yields are more attractive, the ARM dynamically routes capital to external protocols like Morpho (on Ethereum deployments) and Silo (on Sonic deployments) to earn additional yield.

\[ARM Flow of Funds Diagram]

This creates a self-balancing mechanism that narrows peg spreads, restores market efficiency, and keeps liquidity productive in all market conditions. The ARM effectively transforms volatility into opportunity, capturing price spreads between LSTs and their backing collateral.
