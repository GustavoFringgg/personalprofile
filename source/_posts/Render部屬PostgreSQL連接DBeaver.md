---
title: Render部屬PostgreSQL連接DBeaver
date: 2024-12-11 22:59:29
tags:
  - PostgreSQL
  - Render
  - DBeaver
---

### 前言

要把小專案的 side project 資料庫從 mongoDB 移到 PostgreSQL 上
當初想說應該沒有很困難，但果然傳聞說環境設定最麻煩...

<!--more-->

光登入填入資料就花了我很多的時間，怎麼試都不行
趁記憶猶新，趕緊來記錄一下

--

```js sample.js 測試
var foo = function (bar) {
  return bar++;
};

console.log(foo(5));
```

首先我們為了要部屬 PostgreSQL，直接上 render 註冊並開啟專案
最後他會給你一組私人金鑰

<img src="https://firebasestorage.googleapis.com/v0/b/theodore-s-blog.appspot.com/o/DBeaver%E9%80%A3%E6%8E%A5reder%20PosgreSQL%2Frender.jpg?alt=media&token=04666869-517d-41bd-9d86-f5d7e50de89a" alt="範例圖" width="800">

紅框中的資料都是會需要用到的，等等會說怎麼套用上 DBeaver

隨後開啟 DBeaver，開啟連線，並輸入 render 先前提供的金鑰

<img src="https://firebasestorage.googleapis.com/v0/b/theodore-s-blog.appspot.com/o/DBeaver%E9%80%A3%E6%8E%A5reder%20PosgreSQL%2FDBeaver.jpg?alt=media&token=87d45d06-2cf7-4e8d-85da-529baaae46de" alt="範例圖"  width="800">

DBeaver Database = render 的 Database (碼了前面忘記後面)
DBeaver Username = render 的 Username
DBeaver password = render 的 password

這裡最重要的就是那個 Host，起初以為跟 render 的 Hostname 一樣(菜就該死)
怎麼試都不對，GPT 不行，render 社群不行，stackoverflow 也不是我要的
結果最後在一個葡萄牙小哥的 youtube 影片上找到答案...

<font color=#FF0000>DBeaver 所需要的 Host 就在 render 的 PSQL Command 裡</font>
他的組成會是這樣
PGPASSWORD= 你的密碼 psql -h <font color=#FF0000>你的 Host</font> -U 你的 Username 你的 Database

接著把 render 給你的 Host 填入 DBeaver 的 Host，就連線成功了

<img src="https://firebasestorage.googleapis.com/v0/b/theodore-s-blog.appspot.com/o/DBeaver%E9%80%A3%E6%8E%A5reder%20PosgreSQL%2F1733928869828.jpg?alt=media&token=6151a54f-9c45-4cad-94fb-9e3690167177" alt="範例圖"  width="800">

只能說當下真的是有滿滿的感動，此篇記錄了自己的學習過程，也希望能幫助到需要幫助的人
