# OS ARM

### Intro to OS ARM

Origin’s Automated Redemption Manager (ARM) is now live on Sonic.

Origin’s OS ARM offers depositors a low-risk, passive yield strategy. This is Origin’s next ARM deployment, following the successful launch of the stETH ARM vault on Ethereum, which arbitrages the stETH redemption queue. The OS ARM applies the same redemption-based strategy on Sonic, capturing yield from LST peg volatility, supporting the OS peg, and leveraging new efficiencies unique to Sonic’s architecture.

## How it works

Origin’s ARMs earn yield by arbitraging LST prices during times of volatility. When OS trades at a discount, the OS ARM purchases OS on AMMs and deposits it to the Sonic staking withdrawal queue. Once the tokens are redeemed 1:1 for S, the process repeats—generating low-risk yield in the process.

#### Lending Market Integrations

The OS ARM increases its capital efficiency with lending market integrations. In addition to earning yield from arbitraging S redemptions, the OS ARM routes its idle S liquidity to Silo’s lending markets to earn additional yield, unlocking additional upside for depositors even during low-volatility periods.

#### Flow of Funds

1. LP deposits S into the OS ARM vault [using the Origin dapp](https://app.originprotocol.com/#/arm/146:ARM-WS-OS)&#x20;
2. S deposited in the vault is split between:
   * Vault buffer (up until the required liquidity threshold is met)
   * SILO (anything beyond the required vault liquidity goes here to earn lending market yield)
3. S in the vault buffer is used by the ARM to acquire OS at a discount&#x20;
4. OS is placed in the S unstaking queue and redeemed 1:1 for S (the delta between the discounted price and the 1:1 price accrues as yield to the OS ARM)
5. \[Back to Step 2] Resulting S is split between the vault buffer and the lending market &#x20;

### Redemptions

Withdrawals from the ARM are processed on demand when liquidity is available. However, because LSTs must be redeemed through Sonic’s withdrawal queue, redemptions may take up to 14 days during times of high activity.

### DEX Aggregator Integrations

By offering the best rates for OS swaps, the ARM S Vault captures volume from DEX aggregators. The ARM S Vault is integrated with KyberSwap and OpenOcean at launch, two of the leading DEX aggregators on Sonic.
