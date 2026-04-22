# Yield Collection (Harvester)

Origin's yield-bearing tokens accumulate rewards through external strategies — validator incentives, lending market interest, liquidity provision fees, and token emissions from integrated protocols.&#x20;

These rewards accrue in different forms and locations and must be collected and converted to the protocol's base collateral before they can be reflected in holder balances through a rebase. This collection and conversion process is handled by the Harvester.

The Harvester is operated by a 2-of-8 multisig. Two Harvester contracts are deployed: a Standard Harvester for routine operations, and a CoW Harvester that routes swaps through CoW Protocol for improved execution quality and MEV protection. The appropriate contract is used based on the reward type and prevailing market conditions.

To automate and constrain harvesting operations, a Safe Module is layered on top of the multisig. The Safe Module validates each transaction before execution, enforcing that operators act within defined parameters: swaps must remain within acceptable slippage bounds, interactions are limited to verified assets, and DEX routing is restricted to approved protocols. This means the Harvester cannot be used to extract value or interact with unauthorized contracts, even in the event of a compromised multisig signer.

The Harvester is responsible for reward collection and conversion, not for triggering the rebase itself. Rebases are fired independently through Chainlink Keepers at least once per day, and anyone can call the rebase() function directly on the vault contract at any time. Underlying yield continues to accrue at the strategy level regardless of Harvester activity. A lapse in harvesting delays the point at which accumulated rewards are converted and reflected in holder balances, but does not halt yield\
generation.
