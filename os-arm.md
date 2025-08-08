# OS ARM

## **Intro to OS ARM**

Origin’s Automated Redemption Manager (ARM) is now live on Sonic.

Origin’s OS ARM offers depositors a low-risk, passive yield strategy. This is Origin’s second ARM, following the successful launch of the stETH ARM vault on Ethereum, which arbitrages the stETH redemption queue. The OS ARM applies the same redemption-based strategy on Sonic, capturing yield from LST peg volatility, supporting the OS peg, and leveraging new efficiencies unique to Sonic’s architecture.

## **How it works**

Origin’s ARMs earn yield by arbitraging LST prices. The OS ARM purchases OS from AMMs at a discount and redeems it 1:1 for S —generating low-risk yield in the process.

#### **Lending Market Integrations**

The OS ARM increases its capital efficiency with lending market integrations. In addition to earning yield from arbitraging S redemptions, the OS ARM routes its idle S liquidity to Silo’s lending markets to earn additional yield, unlocking additional upside for depositors even during low-volatility periods.

#### **Flow of Funds**

1. LP deposits S into the OS ARM vault [using the Origin dapp](https://app.originprotocol.com/#/arm/146:ARM-WS-OS)
2. S deposited in the vault is split between:
   * Vault buffer (up until the required liquidity threshold is met)
   * SILO (anything beyond the required vault liquidity goes here to earn lending market yield)
3. S in the vault buffer is used by the ARM to acquire OS at a discount
4. OS is redeemed 1:1 for S via Sonic’s 14 day unstaking process (the delta between the discounted price and the 1:1 price accrues as yield to the OS ARM)
5. \[Back to Step 2] Resulting S is split between the vault buffer and the lending market

## **Redemptions**

Withdrawals from the ARM are processed on-demand when liquidity is available. However, because S must be redeemed through Sonic’s ustaking process which is hardcoded at 14 days, redemptions normally take 14-15 days. In the case that the ARM receives additional user deposits, withdrawal liquidity may be available sooner.

## **DEX Aggregator Integrations**

By offering the best rates for OS swaps, the ARM S Vault captures volume from DEX aggregators. The ARM S Vault is integrated with KyberSwap and OpenOcean at launch, two of the leading DEX aggregators on Sonic.Intro to OS ARM

