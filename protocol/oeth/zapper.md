# Zapper

The OETH Zapper is a convenience contract enabling depositors to use Ether (ETH) to mint OETH. The OETH _Vault_ supports WETH but does not allow direct minting with ETH. This design decision increases security and also reduces the gas costs associated with minting.

### Zapping

The [Origin dapp](https://app.originprotocol.com) supports zapping and minting OETH in a single transaction. Users who come to the dapp with ETH will have their transactions automatically routed to the most economically advantageous contract, whether it’s swapping ETH for OETH via Curve or minting OETH by depositing ETH into the Zapper and subsequently WETH into the Vault automatically.

### Withdrawing

The Zapper contract currently only supports depositing, but any OETH minted via the Zapper is still fully liquid. OETH can be redeemed anytime via the Vault for WETH (subject to a fee of 0.1%). Most users find swapping OETH for ETH on Curve easier and more cost-effective. Redeeming and swapping are both supported by the Origin dapp.

\
