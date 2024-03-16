# 🌀 Bitcoin Address Formats

Native SegWit, Nested SegWit, Taproot, and Legacy are all different Bitcoin address formats or transaction types within the Bitcoin network. Each has its own characteristics and benefits:

1. **Native SegWit (Segregated Witness Bech32):**&#x20;

&#x20;  Wallet Supported: <mark style="color:blue;">**Phantom, Leather, Unisat, Okex Wallet**</mark>

* Native SegWit addresses start with "**bc1**."
* Also known as Bech32 addresses.
* Utilizes the Segregated Witness (SegWit) upgrade, which segregates the witness data from the transaction data, resulting in smaller transaction sizes and lower fees.
* Offers improved security and better scalability compared to legacy addresses.
* Recommended for most transactions due to lower fees and enhanced features.

&#x20;  Example: **bc1qju52hg5v6z0f5ds49p4t33wz8gl88a5cuzx7hf**

2. **Nested SegWit (Pay to Witness Public Key Hash, P2SH-P2WPKH):**

&#x20;  Wallet Supported: <mark style="color:blue;">**Xverse, Unisat, Okex Wallet**</mark>

* Nested SegWit addresses start with "**3.**"
* Combines the SegWit benefits with compatibility for older wallet software that does not support Bech32 addresses.
* Allows for transactions to be sent to a SegWit address even if the sender's wallet doesn't natively support SegWit.
* Transactions to nested SegWit addresses are slightly larger and may have slightly higher fees compared to native SegWit.

&#x20;  Example: **3NeLJQTPMJTZwuyYrMJLYHmtpqT7x8dYsk**

3. **Taproot:**

&#x20;  Wallet Supported: <mark style="color:blue;">**Xverse, Phantom, Unisat, Okex Wallet**</mark>

* Taproot is a proposed Bitcoin improvement that enhances privacy, security, and smart contract capabilities.
* Addresses created with Taproot start with "**bc1p.**"
* Combines multiple spending conditions into one, making complex transactions indistinguishable from simpler ones on the blockchain for improved privacy.
* Expected to reduce transaction fees and enable more advanced smart contracts.

&#x20;  Example: **bc1psd90nx647p00y0zx04kl5sx9sgjcpeeqyh9t8d0j220ssvu250hq20c84a**

4. **Legacy (Pay to Public Key Hash, P2PKH):**

&#x20;  Wallet Supported: <mark style="color:blue;">**Unisat**</mark><mark style="color:blue;">,</mark> <mark style="color:blue;"></mark><mark style="color:blue;">**Okex Wallet , Unisat**</mark>

* Legacy addresses start with "**1.**"
* These are the original Bitcoin addresses and transaction types.
* Larger transaction sizes and typically higher fees compared to SegWit addresses.
* While still widely supported, legacy addresses are less efficient and secure than SegWit addresses.

Example : **1HzCQZtedJ5jbn1YBuqgtkPVwfkjkuzyNR**



NOTE**:** DUE TO SECURITY ISSUES AND COST OPTIMIZATION FOR USERS, WE WILL NOT SUPPORT **LEGACY WALLET**
