---
description: Protecting OUSD from market volatility
---

# Price Oracles

### Stablecoin Pricing

OUSD is designed to stay pegged at $1 and be backed 1:1 with its underlying stablecoins. This is trickier than it sounds because these underlying stablecoins are constantly deviating from their own desired $1 pegs. While the majority of daily fluctuations are minor, there have been major swings in price that have occurred in the past and are likely to occur again in the future.

<table><thead><tr><th width="107">Token</th><th width="160">Low</th><th>High</th><th>Delta</th><th>Source</th></tr></thead><tbody><tr><td>USDC</td><td><p>$0.929222</p><p>Mar 13, 2020</p></td><td><p>$1.11</p><p>Oct 15, 2018</p></td><td>$0.180778</td><td><a href="https://coinmarketcap.com/currencies/usd-coin/">CoinMarketCap</a></td></tr><tr><td>USDC</td><td><p>$0.924188</p><p>Aug 02, 2020</p></td><td><p>$1.17</p><p>May 08, 2019</p></td><td>$0.245812</td><td><a href="https://www.coingecko.com/en/coins/usd-coin">CoinGecko</a></td></tr><tr><td>DAI</td><td><p>$0.945505</p><p>May 10, 2020</p></td><td><p>$1.11</p><p>Mar 13, 2020</p></td><td>$0.164495</td><td><a href="https://coinmarketcap.com/currencies/multi-collateral-dai/">CoinMarketCap</a></td></tr><tr><td>DAI</td><td><p>$0.903243</p><p>Nov 25, 2019</p></td><td><p>$1.22</p><p>Mar 13, 2020</p></td><td>$0.316757</td><td><a href="https://www.coingecko.com/en/coins/dai">CoinGecko</a></td></tr><tr><td>USDT</td><td><p>$0.849809</p><p>Feb 02, 2017</p></td><td><p>$1.21</p><p>May 27, 2017</p></td><td>$0.360191</td><td><a href="https://www.coingecko.com/en/coins/tether">CoinGecko</a></td></tr><tr><td>USDT</td><td><p>$0.572521</p><p>Mar 02, 2015</p></td><td><p>$1.32</p><p>Jul 24, 2018</p></td><td>$0.747479</td><td><a href="https://coinmarketcap.com/currencies/tether/">CoinMarketCap</a></td></tr></tbody></table>

The rebasing function treats 1 stablecoin as 1 OUSD for simplicity and to protect OUSD balances from being affected by the daily fluctuations in the price of the underlying stablecoins. Since the rebase function only counts coins, OUSD balances should only increase.

To mint and redeem the appropriate number of OUSD on entry and exit, the smart contracts must accurately price the DAI, USDC, and USDT entering and exiting the system.

As an added precaution, OUSD never pays more than a dollar for a stablecoin nor sells a stablecoin for less than a dollar. When DAI, USDC, or USDT falls below the $1 peg, [OIP-4](https://github.com/OriginProtocol/origin-dollar/issues/1000) disables the minting of additional OUSD tokens using the de-pegged asset. Oracles giving wrong prices will not result in a reduction in the number of stablecoins held. Gains collected as a result of stablecoins slipping from their peg are redistributed to the remaining holders of OUSD in the form of additional yield.

As a decentralized protocol, OUSD must rely on non-centralized sources for these prices. OUSD uses Chainlink oracles for pricing data for DAI, USDC, and USDT. You can read more about [our decision to work with Chainlink](https://blog.originprotocol.com/how-origin-uses-chainlink-oracles-to-secure-ousd-bff5601e840e) on our blog. The specific Chainlink oracles being utilized are listed in the[ousd-registry.md](../contracts/registry/ousd-registry.md "mention").
