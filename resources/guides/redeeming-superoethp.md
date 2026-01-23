# Redeeming superOETHp

**November 12, 2025:** Super OETH on Plume Is Officially Deprecated. All collateral has been withdrawn from the Beacon Chain to support superOETHp redemptions. This means **Super OETH on Plume no longer earns staking rewards.** Liquidity is now available for direct redemptions of superOETHp.

**January 21, 2026:** Redemptions are no longer available on the Origin Dapp. The Vault is fully funded and able to process any remaining withdrawal requests through the [Plume Explorer.](https://explorer.plume.org/address/0xc8c8F8bEA5631A8AF26440AF32a55002138cB76a)

<table><thead><tr><th width="290.22265625">Contract</th><th>Address</th></tr></thead><tbody><tr><td>superOETHp (ERC-20)</td><td><code>0xFCbe50DbE43bF7E5C88C6F6Fb9ef432D4165406E​</code></td></tr><tr><td>Wrapped Super OETH (ERC-4626)</td><td><code>0x2dE8A403f7A5c6C5161D4a129918Ec9f0b653918​</code></td></tr><tr><td>Plume Vault</td><td><code>0xc8c8F8bEA5631A8AF26440AF32a55002138cB76a</code></td></tr></tbody></table>

### How to Unwrap Super OETH on Plume (wsuperOETHp)

To unwrap Wrapped Super OETH (wsuperOETHp), visit the [Plume explorer](https://explorer.plume.org/token/0x2dE8A403f7A5c6C5161D4a129918Ec9f0b653918?tab=read_write_proxy) and locate the contracts tab under wsuperOETHp. Select "Read/Write proxy" and scroll down to the redeem() function. Enter the amount of wsuperOETHp you wish to unwrap, and click "$$x10^{18}$$." Then, enter the address to receive superOETHp and the owner address currently holding wsuperOETHp. Click "write" and execute the transaction from your wallet to complete the withdrawal request.

**Plume explorer contracts page:**

<figure><img src="../../.gitbook/assets/Screenshot 2026-01-23 at 2.27.13 PM.png" alt=""><figcaption></figcaption></figure>

**redeem() function:**

<figure><img src="../../.gitbook/assets/Screenshot 2026-01-23 at 2.27.47 PM.png" alt=""><figcaption></figcaption></figure>

### How to Redeem Super OETH on Plume (superOETHp)

To redeem Super OETH (superOETHp), visit the Plume explorer and find the [Plume Vault contract.](https://explorer.plume.org/address/0xc8c8F8bEA5631A8AF26440AF32a55002138cB76a?tab=read_write_proxy) From here, click "Read/Write proxy" and scroll down to the requestWithdrawal() function. Enter the amount of superOETHp you'd like to withdrawal, and click "$$x 10^{18}$$" before clicking "write" to request your withdrawal.&#x20;

Once your withdrawal request is submitted, there is a one-day delay before being able to claim your withdrawal request. Once your withdrawal is claimable, head back to the same contracts tab, and find the claimWithdrawal() function. You will need to input your requestWithdrawal ID which can be found under "logs" in your requestWithdrawal transaction details. Once inputted, you can claim your withdrawal by clicking "write" and executing the transaction through your wallet.&#x20;

**Plume Vault contracts page:**&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2026-01-23 at 2.29.31 PM.png" alt=""><figcaption></figcaption></figure>

**requestWithdrawal() function:**

<figure><img src="../../.gitbook/assets/Screenshot 2026-01-23 at 2.30.15 PM.png" alt=""><figcaption></figcaption></figure>

**claimWithdrawal() function:**

<figure><img src="../../.gitbook/assets/Screenshot 2026-01-23 at 2.29.54 PM.png" alt=""><figcaption></figcaption></figure>
