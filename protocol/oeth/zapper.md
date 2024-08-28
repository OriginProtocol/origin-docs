# Zapper

The OETH Zapper is a convenience contract enabling depositors to use Ether (ETH) to mint OETH. The OETH _Vault_ supports WETH but does not allow direct minting with ETH. This design decision increases security and also reduces the gas costs associated with minting.

### Zapping

The [Origin dapp](https://originprotocol.eth.limo) supports zapping and minting OETH in a single transaction. Users who come to the dapp with ETH will have their transactions automatically routed to the most economically advantageous contract, whether it’s swapping ETH for OETH via Curve or minting OETH by depositing ETH into the Zapper and subsequently WETH into the Vault automatically.

### Withdrawing

The Zapper contract currently only supports depositing, but any OETH minted via the Zapper is still fully liquid. OETH can be redeemed 1:1 for ETH at any time (see [redemption.md](redemption.md "mention") for more details).

\
