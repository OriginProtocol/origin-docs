# Yield-Bearing Token Integrations

### Integrating Origin’s Yield-Bearing Tokens

This guide covers protocol-level integrations for Origin’s yield-bearing tokens and their wrapped counterparts. It applies to OUSD, OETH, Super OETH, and OS. All tokens share the same integration behavior.

### Token Behavior

Origin’s yield-bearing tokens are standard ERC-20 tokens. Rebasing is disabled by default in smart contracts. Any contract may permissionlessly enable rebasing by calling `rebaseOptIn()`. Protocols may alternatively request Origin to turn on Yield Forwarding, which redirects rebasing yield to an approved address rather than accruing to the smart contract holding the yield-bearing tokens. Yield Forwarding is available for all of Origin’s yield-bearing tokens and requires approval by the Origin team.

### Wrapped Tokens

Origin provides canonical wrapped versions of its yield-bearing tokens that are ERC-4626 compliant. These wrapped tokens accrue yield through price appreciation rather than rebasing and are commonly used in money markets, vault frameworks, and environments that expect non-rebasing assets. Wrapped tokens are built and maintained by Origin and are the recommended option when ERC-4626 compatibility is required.

### Entry and Exit

The recommended entry path for acquiring Origin yield-bearing tokens is the Origin dapp, which optimizes execution between direct minting and AMM swaps based on the best available rate. Onchain liquidity may also be used for programmatic acquisition where needed.

Redemptions to the backing asset are available at a 1:1 rate through the Origin dapp at all times, and instant redemptions are available when vault liquidity permits. Instant redemptions are typical for smaller withdrawals, while larger exits may benefit from executing multiple withdrawals with smaller size. Coordination with the Origin team is recommended, though not required, to determine the most effective exit paths. For OETH and Super OETH, AMMs provide deep liquidity and low-slippage exits back to ETH and are often used for instant exits.

### AMMs and Yield

Origin yield-bearing tokens do not accrue yield inside AMMs by default. Curve and SwapX support Origin’s Pool Booster feature, which enables yield to be forwarded to gauges to incentivize liquidity providers. AMO activity, when present, is limited to specific Origin-managed pools between yield-bearing tokens and their base assets which helps support token pegs and provide extremely low slippage on swaps.

### Pricing and Oracles

Pricing assumptions depend on the token and integration model. For OETH and Super OETH, many protocols treat the assets as 1:1 with ETH. When explicit oracle pricing is required, Origin assets are supported by Chainlink, Tellor, and Dia Data.

For integrations using wrapped tokens, protocols typically pair their chosen ETH oracle or 1:1 assumption with the exchange rate exposed by the ERC-4626 contract. This applies to all of Origin’s yield-bearing tokens and allows accurate pricing without relying on rebasing behavior.

### Peg Mechanics

Peg stability is maintained through full collateral backing and 1:1 redemptions via the Origin dapp. Arbitrage activity corrects deviations when they occur. In supported pools, the AMO may rebalance liquidity to tighten pricing around peg levels.

### Institutional Considerations

Institutional users may hold Origin yield-bearing tokens directly as ERC-20s or via wrapped ERC-4626 versions, depending on accounting and operational requirements. The Origin dapp provides predictable entry and redemption mechanics, while onchain liquidity offers an instant-exit alternative, particularly for ETH-based tokens. Larger redemptions typically benefit from advance coordination with the Origin team to optimize execution and liquidity sourcing.

### Optional Insurance

Optional third-party insurance coverage is available for select Origin assets. OUSD holders may obtain smart contract coverage through [Nexus Mutual](https://nexusmutual.io/), [Lunos](https://lunos.xyz/), or [OpenCover](https://opencover.com/). Super OETH depeg coverage is available through OpenCover as well. OS exploit and oracle manipulation coverage is available through [Safura](https://www.safura.io/). All insurance products are externally provided, optional, and independently priced.
