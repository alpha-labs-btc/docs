# 🚧 发行例子

<mark style="color:red;">`目标:发行$RUNE。总供应量21,000,000`</mark>

#### 计算协议消息中的第一个数据

协议消息中的第一个数据推送被解码为序列整数。这些整数被解释为(ID, OUTPUT, AMOUNT)元组序列\ 
整数被编码为前缀可变数，其中可变数的前导数决定了其字节长度。有很多类型的前缀变体，这是比特币的[风格](https://en.bitcoin.it/wiki/Protocol\_documentation#Variable\_length\_integer)


要发出21000000符文，我们使用这个元组 <mark style="color:red;">`[0 , 1, 21000000].`</mark>

为什么是 <mark style="color:red;">`[0 , 1, 21000000]`</mark> ?

* [x] 元组中的第一个整数是ID <mark style="color:red;">`0`</mark> 为了发行交易
* [x] 元组中的第二个整数<mark style="color:red;">`1`</mark> 映射到事务的输出索引 
* [x] 元组中的第三个整数是发行金额 <mark style="color:red;">`21000000`</mark>

<figure><img src=".gitbook/assets/Screen Shot 2023-09-27 at 00.18.26.png" alt=""><figcaption></figcaption></figure>

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

这是元组的数据 `[0, 1, 21000000]` 在对  **比特币风格的编码** 解码后\ 


```javascript
0 => 00
1 => 01
21000000 => fe406f4001

[0, 1, 21000000] => 0001fe406f4001
```

#### 计算协议消息中的第一个数据

第二个数据推送被解码为两个整数, `SYMBOL`, `DECIMALS`

`SYMBOL` 是一个26进制编码的人类可读符号，类似于oridinals名称中使用的符号。唯一有效的字符是` A `到` Z `.


oridinals名称是[base-26](https://docs.ordinals.com/bounty/3.html?highlight=base-26#criteria)序数的编码。为了避免将短名字锁定在不可花费的创世区块coinbase奖励中，序数变得越来越短，序数变得越来越长。第一个要挖掘的卫星0的名称是` nvtdijuwxlp `，最后一个要挖掘的卫星2,099,999,997,689,999的名称是` a `。

```javascript
// Some code
const bb26 = require("base26");

const text = 'rune';

const formatOrdinalBase26 = (text) => {
 const result = (2099999997689999 + 1 - bb26.from(text));
 return result;
};

```

这是元组的数据 `[RUNE, 18]` 在对  **比特币风格的编码** 解码后\ 


```javascript
RUNE => 2099999997359067 => ffdbf3de59dbf3de59
18 => 12

[RUNE, 18] => ffdbf3de59dbf3de5912
```

#### 协议消息的最后结果

```
OP_RETURN 52 0001fe406f4001 ffdbf3de59dbf3de5912
```

