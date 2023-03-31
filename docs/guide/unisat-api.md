# Unilite Wallet API

## Table of Contents

[[toc]]

## Methods


### requestAccounts

```typescript
unilite.requestAccounts()
```

Connect the current account.

#### Parameters

none

#### Returns

`Promise` returns `string[]` : Address of current account.

#### Example

```typescript
try {
  let accounts = await window.unilite.requestAccounts();
  console.log('connect success', accounts);
} catch (e) {
  console.log('connect failed');
}
> connect success ['tb1qrn7tvhdf6wnh790384ahj56u0xaa0kqgautnnz']
```


### getAccounts

```typescript
unilite.getAccounts()
```

Get address of current account

#### Parameters

none

#### Returns

* `Promise` - `string`: address of current account

#### Example

```typescript
try {
  let res = await window.unilite.getAccounts();
  console.log(res)
} catch (e) {
  console.log(e);
}
> ["tb1qrn7tvhdf6wnh790384ahj56u0xaa0kqgautnnz"]
```

### getNetwork

```typescript
unilite.getNetwork()
```

get network

#### Parameters

none

#### Returns

* `Promise` - `string`: the network.  `livenet` and `testnet` 

#### Example

```typescript
try {
  let res = await window.unilite.getNetwork();
  console.log(res)
} catch (e) {
  console.log(e);
}

> 0
```

### switchNetwork

```typescript
unilite.switchNetwork(network)
```

switch network

#### Parameters

* `network` - `string`: the network.  `livenet` and `testnet` 

#### Returns

none

#### Example

```typescript
try {
  let res = await window.unilite.switchNetwork("livenet");
  console.log(res)
} catch (e) {
  console.log(e);
}

> 0
```




### getPublicKey

```typescript
unilite.getPublicKey()
```

Get publicKey of current account.

#### Parameters

none 

#### Returns

* `Promise` - `string`: publicKey

#### Example

```typescript
try {
  let res = await window.unilite.getPublicKey();
  console.log(res)
} catch (e) {
  console.log(e);
}
> 03cbaedc26f03fd3ba02fc936f338e980c9e2172c5e23128877ed46827e935296f
```




### getBalance

```typescript
unilite.getBalance()
```

Get BTC balance

#### Parameters

none

#### Returns

* `Promise` - `Object`: 
   - ` confirmed ` - ` number ` : the confirmed satoshis
   - ` unconfirmed ` - ` number ` : the unconfirmed satoshis
   - ` total ` - ` number ` : the total satoshis

  

#### Example

```typescript
try {
  let res = await window.unilite.getBalance();
  console.log(res)
} catch (e) {
  console.log(e);
}

> {
    "confirmed":0,
    "unconfirmed":100000,
    "total":100000
  }
```

### getInscriptions (todo)

```typescript
unilite.getInscriptions()
```

Get Inscriptions (Max to 100)

#### Parameters

none

#### Returns

* `Promise` - `Object[]`: 
   * ` id ` - ` string ` : the id of inscription.
   * ` num ` - ` string ` : the number of inscription.
   * ` address ` - ` string ` : the address of inscription.
   * ` content ` - ` string ` : the content url of inscription.
   * ` content_length` - ` string ` : the content length of inscription.
   * ` content_type ` - ` number ` : the content type of inscription.
   * ` preview ` - ` number ` : the preview link
   * ` timestamp ` - ` number ` : the timestamp of inscription.

#### Example

```typescript
try {
  let res = await window.unilite.getInscriptions();
  console.log(res)
} catch (e) {
  console.log(e);
}

> [
  ...
]
```



### sendLitecoin

```typescript
unilite.sendBitcoin(toAddress, satoshis)
```

Send LTC

#### Parameters

* `toAddress` - `string`: the address to send
* `satoshis` - `number`: the satoshis to send


#### Returns

* `Promise` - `string`: txid

#### Example

```typescript
try {
  let txid = await window.unilite.sendLitecoin("tb1qrn7tvhdf6wnh790384ahj56u0xaa0kqgautnnz",1000);
  console.log(txid)
} catch (e) {
  console.log(e);
}
```

### sendInscription (todo)

```typescript
unilite.sendInscription(options)
```

Send Inscription

#### Parameters

* `options` - `Object`:
    - `id` - `string`: the id of Inscription.
    - `address` - `string`:  the receiver address.

#### Returns

* `Promise` - `Object`: 
  + `txid` - `string` : the txid

#### Example

```typescript
try {
  let {txid} = await window.unilite.sendInscription({
    id:"e9b86a063d78cc8a1ed17d291703bcc95bcd521e087ab0c7f1621c9c607def1ai0",
    address:"tb1q8h8s4zd9y0lkrx334aqnj4ykqs220ss7mjxzny"
  });
  console.log("send Inscription 204 to tb1q8h8s4zd9y0lkrx334aqnj4ykqs220ss7mjxzny",{txid})
} catch (e) {
  console.log(e);
}
```

### signMessage

```typescript
unilite.signMessage(msg[, address])
```

sign message

#### Parameters

* `msg` - `string`: a string to sign

#### Returns

* `Promise` - `string`: the signature.

#### Example

```typescript
try {
  let res = await window.unilite.signMessage("abcdefghijk123456789");
  console.log(res)
} catch (e) {
  console.log(e);
}

> IMEo3yzgqJKlmc38IqlP3YjadVOnXmVR6fqeDhtVdiyHUbitYlO2CFUHUgGtM1/cjWsWoGVhTv6pyvj9L/kNT5A=
```

### signTx (todo)

```typescript
unilite.signTx(txHex, inputInfos)
```

Sign transaction

#### Parameters

* `txHex` - `string`: the hex raw transaction to sign
* `inputInfos` - `Object[]`: the inputs to sign
  + `inputIndex` - `number`: the index of input 
  + `scriptHex` - `string`: the previous output script of input 
  + `satoshis` - `number`: the previous output satoshis of input
  + `sighashType` - `number`: the sighash type
  + `address` - `number|string`: the address of account

#### Returns

* `Promise` - `SigResult[]`: 
  + `sig` - `string`: the signature 
  + `publicKey` - `string`: the publicKey of account

#### Example

```typescript
try {
  let res = await window.unilite.signTx("",[]);
  console.log(res)
} catch (e) {
  console.log(e);
}
```

### pushTx

```typescript
unilite.pushTx(options)
```

Push Transaction

#### Parameters

* `options` - `Object`:
    - `rawtx` - `string`:  rawtx to push

#### Returns

* `Promise` - `string`: txid

#### Example

```typescript
try {
  let txid = await window.unilite.pushTx({
    rawtx:"0200000000010135bd7d..."
  });
  console.log(txid)
} catch (e) {
  console.log(e);
}
```




### signPsbt

```typescript
unilite.signPsbt(psbtHex)
```

Sign PSBT  

This method will traverse all inputs that match the current address to sign.

#### Parameters

* `psbtHex` - `string`: the hex string of psbt to sign

#### Returns

* `Promise` - `string`:  the hex string of signed psbt 

#### Example

```typescript
try {
  let res = await window.unilite.signPsbt("70736274ff01007d....");
  console.log(res)
} catch (e) {
  console.log(e);
}
```

### pushPsbt

```typescript
unilite.pushPsbt(psbtHex)
```
Push transaction
#### Parameters

* `psbtHex` - `string`: the hex string of psbt to push

#### Returns

* `Promise` - `string`: txid

#### Example

```typescript
try {
  let res = await window.unilite.pushPsbt("70736274ff01007d....");
  console.log(res)
} catch (e) {
  console.log(e);
}
```

## Events


### accountsChanged

```typescript
unilite.on('accountsChanged', handler: (accounts: Array<string>) => void);
unilite.removeListener('accountsChanged', handler: (accounts: Array<string>) => void);
```

The `accountsChanged` will be emitted whenever the user's exposed account address changes.



### networkChanged

```typescript
unilite.on('networkChanged', handler: (network: string) => void);
unilite.removeListener('networkChanged', handler: (network: string) => void);
```

The `networkChanged` will be emitted whenever the user's network changes.


