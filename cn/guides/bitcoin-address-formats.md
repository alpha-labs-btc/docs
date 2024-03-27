# 比特币地址格式

原生隔离见证、嵌套隔离见证、Taproot和Legacy都是比特币网络中不同的比特币地址格式或交易类型。每一种都有自己的特点和好处:

1. **本地隔离见证(Segregated Witness Bech32):**

钱包的支持 <mark style="color:blue;">**Phantom, Leather, Unisat, Okex Wallet**</mark>

* 本地隔离见证地址以 "**bc1**."开始
* 也称为Bech32地址.
* 利用隔离见证(SegWit)升级，将见证数据从交易数据中分离出来，从而减少交易规模和降低费用。.
* 与遗留地址相比，提供了改进的安全性和更好的可伸缩性.
* 由于较低的费用和增强的功能，建议用于大多数交易.

举例: **bc1qju52hg5v6z0f5ds49p4t33wz8gl88a5cuzx7hf**

2. **嵌套隔离见证(付费见证公钥哈希，P2SH-P2WPKH):**

钱包的支持: <mark style="color:blue;">**Xverse, Unisat, Okex Wallet**</mark>

* 嵌套的隔离见证地址以 "**3.**"开始
* 将SegWit的优点与不支持Bech32地址的旧钱包软件的兼容性结合起来.
* 允许交易发送到隔离见证地址，即使发送者的钱包本身不支持隔离见证.
* 与本地SegWit相比，嵌套SegWit地址的交易略大，费用可能略高.

例子: **3NeLJQTPMJTZwuyYrMJLYHmtpqT7x8dYsk**

3. **Taproot:**

钱包的支持: <mark style="color:blue;">**Xverse, Phantom, Unisat, Okex Wallet**</mark>

* Taproot是比特币的一项改进提议，可增强隐私、安全性和智能合约功能.
* 用Taproot创建的地址以"**bc1p.**"开始
* 将多个支出条件合并为一个，使复杂的交易与区块链上的简单交易无法区分，以提高隐私性.
* 预计将降低交易费用，并实现更先进的智能合约.

例子: **bc1psd90nx647p00y0zx04kl5sx9sgjcpeeqyh9t8d0j220ssvu250hq20c84a**

4. **Legacy (Pay to Public Key Hash, P2PKH):**

钱包的支持: <mark style="color:blue;">**Unisat**</mark><mark style="color:blue;">,</mark> <mark style="color:blue;">**Okex Wallet , Unisat**</mark>

* Legacy 地址以 "**1.**"开始
* 这些是原始比特币地址和交易类型.
* 与SegWit地址相比，交易规模更大，通常费用更高.
* 虽然仍然得到广泛支持，但传统地址的效率和安全性不如SegWit地址.

例子 : **1HzCQZtedJ5jbn1YBuqgtkPVwfkjkuzyNR**

注意\*\*:\*\* 由于安全问题和成本优化的用户，我们将不支持**LEGACY 钱包**
