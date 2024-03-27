# 🚧 Issuance example

<mark style="color:red;">`Goal: Issuance $RUNE. total supply 21,000,000`</mark>

#### Calculate the first data in protocol message

The first data push in a protocol message is decoded as a sequence integers. These integers are interpreted as a sequence of (ID, OUTPUT, AMOUNT) tuples\
Integers are encoded as prefix varints, where the number of leading ones in a varint determines its length in bytes. There is many types of prefix varints, and here is the Bitcoin [style](https://en.bitcoin.it/wiki/Protocol\_documentation#Variable\_length\_integer)\


To issue 21000000 rune we use this tuple <mark style="color:red;">`[0 , 1, 21000000].`</mark>

But why <mark style="color:red;">`[0 , 1, 21000000]`</mark> ?

* [x] First Integer in tuple is ID <mark style="color:red;">`0`</mark> for Issuance transaction
* [x] Second Integer in tuple mapped to output index <mark style="color:red;">`1`</mark> of transaction
* [x] Third  Integer in tuple is amount to issue <mark style="color:red;">`21000000`</mark>

<figure><img src="../.gitbook/assets/Screen Shot 2023-09-27 at 00.18.26.png" alt=""><figcaption></figcaption></figure>

```javascript
function encodeBitcoinVarInt(value) {
  if (value < 0xfd) {
    return [value];
  } else if (value <= 0xffff) {
    return [0xfd, value & 0xff, (value >> 8) & 0xff];
  } else if (value <= 0xffffffff) {
    return [0xfe, value & 0xff, (value >> 8) & 0xff, (value >> 16) & 0xff, (value >> 24) & 0xff];
  } else {
    return [
      0xff,
      value & 0xff,
      (value >> 8) & 0xff,
      (value >> 16) & 0xff,
      (value >> 24) & 0xff,
      (value >> 32) & 0xff,
      (value >> 40) & 0xff,
      (value >> 48) & 0xff,
      (value >> 56) & 0xff,
    ];
  }
}

function encodeBitcoinVarIntTuple(tuple) {
  const encodedBytes = tuple.map(encodeBitcoinVarInt).flat();

  // Convert the bytes to a hexadecimal string
  const hexString = encodedBytes.map(byte => byte.toString(16).padStart(2, '0')).join('');

  return hexString;
}
```

Here is data of tuple `[0, 1, 21000000]` after  **prefix varints Bitcoin-style** encode\


```javascript
0 => 00
1 => 01
21000000 => fe406f4001

[0, 1, 21000000] => 0001fe406f4001
```

#### Calculate the first data in protocol message

The second data push is decoded as two integers, `SYMBOL`, `DECIMALS`

`SYMBOL` is a base 26-encoded human readable symbol, similar to that used in ordinal number sat names. The only valid characters are `A` through `Z`.

Ordinal names are a modified [base-26](https://docs.ordinals.com/bounty/3.html?highlight=base-26#criteria) encoding of ordinal numbers. To avoid locking short names inside the unspendable genesis block coinbase reward, ordinal names get _shorter_ as the ordinal number gets _longer_. The name of sat 0, the first sat to be mined is `nvtdijuwxlp` and the name of sat 2,099,999,997,689,999, the last sat to be mined, is `a`.

```javascript
// Some code
const bb26 = require("base26");

const text = 'rune';

const formatOrdinalBase26 = (text) => {
 const result = (2099999997689999 + 1 - bb26.from(text));
 return result;
};

```

Here is data of tuple `[RUNE, 18]` after  **prefix varints Bitcoin-style** encode\


```javascript
RUNE => 2099999997359067 => ffdbf3de59dbf3de59
18 => 12

[RUNE, 18] => ffdbf3de59dbf3de5912
```

#### Last result  of Protocol message

```
OP_RETURN 52 0001fe406f4001 ffdbf3de59dbf3de5912
```

