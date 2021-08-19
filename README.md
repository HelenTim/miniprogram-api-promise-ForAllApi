# miniprogram-api-promise

[![](https://img.shields.io/npm/v/miniprogram-api-promise.svg?style=flat)](https://www.npmjs.com/package/miniprogram-api-promise)
[![](https://img.shields.io/github/license/wechat-miniprogram/api-typings.svg)](https://github.com/wechat-miniprogram/miniprogram-api-promise)

Extend WeChat miniprogram's api to surport promise.

# Installation

```
npm install --save miniprogram-api-promise-forallapi
```

# Getting started
Call the method promisifyAll at the program entry (app.js), It only needs to be called once.
The package on the wechat official website does not convert all APIs to promise, but it can be used here

💨example:
```
import { promisifyAll, promisify } from 'miniprogram-api-promise-forallapi';

const wxp = {}
// promisify all wx's api
promisifyAll(wx, wxp)
console.log(wxp.getSystemInfoSync())
wxp.getSystemInfo().then(console.log)
wxp.showModal().then(wxp.openSetting())

// compatible usage
wxp.getSystemInfo({success(res) {console.log(res)}})

// promisify single api
promisify(wx.getSystemInfo)().then(console.log)

// even if wx.getAccountInfoSync is not a promise interface，but we can still use it like this。
wxp.getAccountInfoSync().then(console.log)

// We can also use it like this
promisify('not a functoin').then(console.log)
```
