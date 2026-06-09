# Introduction to ARM

<figure><img src="../.gitbook/assets/origin arm (1).png" alt=""><figcaption></figcaption></figure>

The Automated Redemption Manager (ARM) is Origin’s onchain liquidity engine designed to enable better exit liquidity and tighter pegs for yield-bearing assets such as stETH, eETH, and OS. The ARM continuously arbitrages between secondary market prices and the token’s underlying collateral to help tokens trade close to their underlying value.

By automating the redemption process, the ARM provides deep, efficient liquidity without relying on centralized market makers. It sources and deploys capital directly from ARM Vaults, generating sustainable yield from arbitrage activity while reinforcing price stability for yield-bearing tokens.

The result is a mechanism that strengthens liquidity across multiple protocols, improves capital efficiency, and enhances the overall stability of Ethereum’s liquid staking and yield-bearing token markets.

### **How the ARM Works**

When a liquid staking token trades below its redemption value, the ARM buys it on secondary markets and redeems it for the underlying asset directly through the protocol’s withdrawal process.

When market spreads tighten and lending yields are more attractive, the ARM dynamically routes capital to external protocols like Morpho (on Ethereum deployments) and Silo (on Sonic deployments) to earn additional yield.

WETH from the stETH and eETH ARM Vaults is sent to the [Morpho WETH ARM Vault](https://app.morpho.org/ethereum/vault/0x3Dfe70B05657949A5dB340754aD664810ac63b21/weth-arm-vault) to earn yield when arbitrage opportunities are not present. The vault lends to top ETH-denominated markets on Morpho, with the majority of WETH being used across wrapped stETH and wrapped eETH Morpho markets.

ARM rebalancing is buffer-driven. Idle liquidity can be allocated to external lending markets when it is not needed for immediate swap/redemption activity, while the configured ARM buffer determines how much liquidity remains available in the vault. Rebalancing around this buffer can be triggered permissionlessly through the allocate() fuction.

**ARM Flow of Funds**

<figure><img src="../.gitbook/assets/ARM Vault Diagram.png" alt=""><figcaption></figcaption></figure>

This creates a self-balancing mechanism that narrows peg spreads, restores market efficiency, and keeps liquidity productive in all market conditions. The ARM effectively transforms volatility into opportunity, capturing price spreads between LSTs and their backing collateral.

### Historical Yield Performance

During its first year of operation, the stETH ARM averaged 4.06% APY, approximately 50% above the average ETH liquid staking return of 2.67% over the same period. ARM yield is substantially more volatile than staking rewards, reflecting the strategy's dependence on secondary market pricing conditions.&#x20;

ARM yield is variable because capital rotates between redemption arbitrage and lending-market yield. In quiet markets, yield trends toward the lending-market baseline. During larger peg dislocations, redemption arbitrage can become the dominant source of returns.

The lending floor and volatility ceiling together define the ARM's yield range: a persistent baseline from Morpho, with upside captured from market dislocations.
