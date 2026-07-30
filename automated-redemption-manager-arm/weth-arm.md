---
description: >-
  Origin Protocol’s multi-asset automated redemption manager earns
  ETH-denominated yield through passive arbitrage between liquid staking token
  market prices and redemption values.
---

# WETH ARM

### WETH ARM: Introduction

Origin's WETH ARM offers LPs a passive way to earn yield on ETH through redemption arbitrage and lending market yield.

The WETH ARM is a multi-asset ETH Vault that uses one shared pool of WETH to quote atomic liquidity for stETH, wstETH, eETH, and weETH. This allows one vault position to participate across multiple liquid staking markets without splitting LP liquidity between separate vaults.

Each supported asset maintains its own pricing, liquidity limits, inventory accounting, pending redemptions, and redemption adapter.

#### How it Works

The WETH ARM continuously quotes WETH prices for each supported asset. When a quote is competitive, traders can sell stETH, wstETH, eETH, or weETH to the vault.

Acquired inventory then moves through the corresponding redemption process:

* stETH is redeemed for ETH through the Lido redemption queue.
* wstETH is unwrapped into stETH before entering the Lido redemption queue.
* eETH is redeemed for ETH through ether.fi's redemption process.
* weETH is unwrapped into eETH before entering ether.fi's redemption process.

The difference between the WETH paid to acquire an asset and the ETH returned through redemption accrues as yield to WETH ARM LPs.

Because all four assets draw from the same WETH liquidity, the vault can respond to opportunities across multiple markets. Prices and liquidity limits remain separate for every supported asset.

#### Lending Market Integrations

The WETH ARM increases its capital efficiency through a Morpho lending integration.

When WETH is not required for redemption arbitrage or going through the withdrawal process, it is routed to the Morpho WETH ARM Vault used by the stETH and eETH ARMs. This allows idle vault liquidity to earn lending market yield during periods when spreads are tight and fewer arbitrage opportunities are available.

WETH can be pulled from Morpho as the vault requires additional liquidity for quotes or withdrawals.

#### Flow of Funds

1. An LP deposits WETH into the WETH ARM Vault using the [Origin dapp.](https://app.originprotocol.com/#/arm/1:ARM-WETH)
2. WETH liquidity in the vault is split between:
   * The vault buffer, which supports quotes and withdrawals
   * The Morpho WETH ARM Vault, where idle liquidity earns lending market yield
3. Traders swap against the vault's WETH quotes for stETH, wstETH, eETH, or weETH.
4. Acquired inventory moves through its corresponding redemption adapter.
5. ETH returned through redemption is converted to WETH and allocated between the vault buffer and the Morpho WETH Vault.
6. The process repeats as new trades clear the vault's quotes.

#### Redemptions

Withdrawals from the WETH ARM are processed on demand when sufficient WETH liquidity is available.

After a redemption request is submitted, the withdrawal may become claimable following the standard 10-minute delay. If the vault does not have enough available WETH, the request remains pending until liquidity returns from Morpho, new LP deposits, or an underlying asset redemption.

Withdrawal timing depends on the vault's current inventory and the redemption rail being used:

| **Asset**     | Redemption Length (normal conditions) | Redemption Length (stressed conditions) |
| ------------- | ------------------------------------- | --------------------------------------- |
| WETH          | 10-minute delay                       | 10-minute delay                         |
| stETH, wstETH | 1-2 days                              | 5-14 days                               |
| eETH, weETH   | 1-5 days                              | 7-15 days                               |

Additional deposits or WETH returning from Morpho may make withdrawal liquidity available sooner.

#### LP Token

The WETH ARM LP token is `ARM-WETH`.

Users who deposit into the WETH ARM Vault receive `ARM-WETH`, representing their proportional share of the vault. Yield accrues through increases in the LP token's exchange rate rather than changes to the token balance.

**Contract:** [0x68025A4615407993A680102b08a23A61D11C657C](https://etherscan.io/address/0x68025A4615407993A680102b08a23A61D11C657C)

**Origin dapp:** [https://app.originprotocol.com/#/arm/1:ARM-WETH](https://app.originprotocol.com/#/arm/1:ARM-WETH)

**Analytics:** [https://analytics.originprotocol.com/arm/1:ARM-WETH](https://analytics.originprotocol.com/arm/1:ARM-WETH)

### **Performance Fee**

Origin charges a 20% performance fee on yield generated from arbitrage activity on the WETH ARM. No fees are charged on lending market yields earned by the vault.

This fee is deducted from gross yield before distributions are made to depositors; it does not apply to principal. Net protocol fees are directed to OGN buybacks, which flow to xOGN stakers, creating a direct link between protocol revenue and token holder value. The APYs displayed on Origin's analytics dashboard and third-party tracking platforms reflect net returns after this fee has been applied, so the figures represent what depositors actually earn.
