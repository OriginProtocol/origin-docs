# Staking (xOGN)

OGN staking converts liquid OGN into xOGN, a locked position that concentrates both governance and economic power in long-term participants. Stakers commit their OGN for a chosen lock period between one month and one year, receiving xOGN in exchange. Longer locks earn higher voting weight and a larger share of protocol fees.

Net protocol fees are directed to OGN stakers. These fees are used to buy back OGN on the open market and distribute it to xOGN, creating a direct link between protocol revenue and staking yield. Rewards accrue continuously and can be claimed at any time without unlocking the underlying position.

xOGN holders can create and vote on governance proposals, set parameters for Origin products, and influence how protocol-controlled value and future incentives are deployed across the ecosystem.

## **Economic & Voting Power Calculation**

Staking converts OGN into xOGN based on two inputs: the amount staked and the lock duration. You can choose lock durations between 30 days and 1 year. You can unstake at any time, but exiting before the selected lock end date applies an early-unstake penalty.

A time-based multiplier is applied to your OGN based on how long you lock for. Longer locks receive a higher multiplier and therefore more xOGN. What matters is how much time is left until unlock. As time passes and your lock approaches expiry, your effective multiplier and voting power gradually decrease. For example, if two users each lock the same amount of OGN for one year, the user whose lock expires later (because they staked more recently) will have slightly more voting power at a given point in time, since they still have more remaining lock time.

The multiplier curve is exponential and grows by roughly 1.4x over one year. A 1-year lock receives about 1.4x the xOGN of a 30-day lock for the same OGN amount. Extending an existing stake works the same way: pushing your end date forward by one year immediately applies the additional 1.4x factor to the xOGN associated with that stake.

As new stakes with longer expirations enter the system, older stakes are gradually diluted in relative influence by comparison. Once your lock duration expires, your xOGN and its associated voting and economic power remain in place until you choose to unstake. To maximize influence, stakers typically keep their positions locked near the maximum duration, periodically extend their expiry, and restake claimed rewards to grow their xOGN balance over time.

## **Comparing xOGN to veCRV**

The [Curve Finance](https://curve.finance/) veCRV model inspired the design of xOGN. Both systems grant greater voting and economic power to participants who lock tokens for longer durations. Origin built on this concept while simplifying the implementation and lowering gas costs, adding flexibility to staking and governance.

Key differences between xOGN and veCRV include:

* **Multiple stakes per address:** OGN holders can create multiple stakes with different lock durations from the same Ethereum account.
* **Delegated governance:** OGN stakers can delegate voting power, enabling separation of custody (cold storage or custodial wallets) from active governance (hot wallets).
* **Exponential decay:** xOGN applies an exponential decay function for voting power, rather than veCRV’s linear schedule.
* **Non-decreasing balances:** veCRV balances decrease over time and reach zero at expiry. xOGN balances remain constant; their relative share of total voting power declines as remaining lock time shortens and new, longer-dated stakes are created.

OGN staking is available through the [Origin dapp](https://app.originprotocol.com/#/ogn/staking).
