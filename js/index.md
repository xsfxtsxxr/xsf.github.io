### 2020-2-26

#### 1.toString 实现随机数

```js
Math.random().toString(36).substr(2)
```

#### 2.返回一个在指定值之间的随机数。这个值不小于  min（有可能等于），并且小于（不等于）max

```js
const ret = Math.random() * (max - min) + min

min =< ret < max
```

#### 3.CryptoJS 使用加密

```js
// crypto.js
import CryptoJS from 'crypto-js'
const CRYPTOJSKEY = CryptoJS.enc.Utf8.parse('hzfpasswordaesky')
const CRYPTOJSIV = CryptoJS.enc.Utf8.parse('ABCDEF1234123412')
const OPTIONS = {
  iv: CRYPTOJSIV,
  mode: CryptoJS.mode.ECB,
  padding: CryptoJS.pad.Pkcs7,
}

export function Encrypt(word) {
  var encryptedData = CryptoJS.AES.encrypt(
    JSON.stringify(word),
    CRYPTOJSKEY,
    OPTIONS
  )
  var encryptedBase64Str = encryptedData.toString()
  return encryptedBase64Str
}

export function Decrypt(word) {
  var decryptedData = CryptoJS.AES.decrypt(word, CRYPTOJSKEY, OPTIONS)
  var decryptedStr = decryptedData.toString(CryptoJS.enc.Utf8)
  return decryptedStr
}

// 使用方式：

import { Encrypt, Decrypt } from '@/libs/crypto.js'

setPassword(Encrypt(values.password)) // 加密保存

Decrypt(getPassword()) // 解密输出
```
