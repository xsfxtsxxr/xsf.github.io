### 2020-2-26

#### 1.toString 实现随机数

```js
Math.random().toString(36).substr(2);
```

#### 2.返回一个在指定值之间的随机数。这个值不小于  min（有可能等于），并且小于（不等于）max

```js
const ret = Math.random() * (max - min) + min

min =< ret < max
```

#### 3.CryptoJS 使用加密

```js
// crypto.js
import CryptoJS from "crypto-js";
const CRYPTOJSKEY = CryptoJS.enc.Utf8.parse("hzfpasswordaesky");
const CRYPTOJSIV = CryptoJS.enc.Utf8.parse("ABCDEF1234123412");
const OPTIONS = {
  iv: CRYPTOJSIV,
  mode: CryptoJS.mode.ECB,
  padding: CryptoJS.pad.Pkcs7,
};

export function Encrypt(word) {
  var encryptedData = CryptoJS.AES.encrypt(
    JSON.stringify(word),
    CRYPTOJSKEY,
    OPTIONS
  );
  var encryptedBase64Str = encryptedData.toString();
  return encryptedBase64Str;
}

export function Decrypt(word) {
  var decryptedData = CryptoJS.AES.decrypt(word, CRYPTOJSKEY, OPTIONS);
  var decryptedStr = decryptedData.toString(CryptoJS.enc.Utf8);
  return decryptedStr;
}

// 使用方式：

import { Encrypt, Decrypt } from "@/libs/crypto.js";

setPassword(Encrypt(values.password)); // 加密保存

Decrypt(getPassword()); // 解密输出
```

#### 4.模拟异步方法

```js
testFunction() {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve();
    }, 3000);
  });
}
```

### 2020-3-1

#### awaitTo-js 解决 await 捕获错误信息

```js
// @params {Function} promise await后面的函数

const awaitTo = (promise) => {
  return promise
    .then((data) => {
      return [null, data];
    })
    .catch((err) => {
      return [err];
    });
};

const [error, data] = await awaitTo(Promise.resolve("success"));
if (error) {
  console.log("error", error);
} else {
  console.log(data);
}
```

### 2021-9-24

#### polyfill Promise.allSettled

```js
export const allSettled = (promises) => {
  if (!Promise.allSettled) {
    return Promise.all(
      promises.map((promise) =>
        promise
          .then((value) => ({ status: "fulfilled", value }))
          .catch((reason) => ({ status: "rejected", reason }))
      )
    );
  }
  return Promise.allSettled(promises);
};
```

### 2021-12-1

#### ASCII 正则

```js
const asciiRegex = /^[\x00-\x7f]*$/;
```

### 2021-12-6

#### 1.用 setTimeout 代替 setInterval

```js
const timeFun = (ms) => {
  setTimeout(function () {
    // 这里不可以用箭头函数，否则无法使用arguments.callee函数，就得用timeFun指定函数名
    console.log(new Date().toLocaleTimeString());
    // setTimeout(timeFun, ms);
    setTimeout(arguments.callee, ms);
  }, ms);
};
```

#### 2.防抖节流函数

```js
// 防抖：短时间内大量触发同一事件，只会执行一次函数
function debounce(fn, time) {
  let timer = null;
  return function () {
    // 不可以用箭头函数，否则下面的arguments不可用
    let context = this; // 放里面， 符合用户调用习惯
    let args = [...arguments];
    if (timer) {
      clearTimeout(timer);
      timer = null;
    }
    timer = setTimeout(() => fn.apply(context, args), time);
  };
}

// 节流： 在指定时间内只执行一次

// 1.定时器方案
function throttle1(fn, time) {
  let timer = null,
    first = true;
  return function () {
    const context = this;
    const args = [...arguments];
    if (first) {
      // 第一次执行
      first = false;
      fn.call(context, args);
    }
    if (!timer) {
      timer = setInterval(() => {
        fn.apply(this, args);
        timer = null;
        clearInterval(timer);
      }, time);
    }
  };
}

// 2.时间戳方案
function throttle2(fn, wait) {
  var pre = Date.now();
  return function () {
    var context = this;
    var args = [...arguments];
    var now = Date.now();
    if (now - pre >= wait) {
      fn.apply(context, args);
      pre = Date.now(); // 更新初始时间
    }
  };
}
```

#### 3.平级节点转树节点

```js
const flatToTree = (arr, id, key = "parentId") => {
  return arr
    .filter((item) => item[key] === id)
    .map((item) => ({ ...item, children: flatToTree(arr, item.id) }));
};

const treeData = flatToTree(flatData);
```
