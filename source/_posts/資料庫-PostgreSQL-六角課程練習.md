---
title: 資料庫-PostgreSQL 六角課程練習
date: 2024-11-01 10:09:59
tags:
  - PostgreSQL
---

### 前言

經過了半年的體驗營，途中經歷了各種前後端的技術洗禮，看到六角推出的後端資料庫體驗營

實在太佛了，所以重拾之前學到的ＨＥＸＯ架站，開始自己的學習文章撰寫紀錄

這是一個 PostgreSQL 的資料庫學習旅程

<!--more-->

### <font color=#FF0000>什麼是 PostgreSQL ?</font>

一種強大的開源關聯式資料庫管理系統（RDBMS），通常簡稱為 "Postgres"。它以強大的功能、穩定性和擴展性聞名，並且支援標準的 SQL 語法，而它有以下特點

1. 資料完整性和高可用性
   支援事務處理（ACID 原則），能夠保證資料的完整性與一致性，適合需要高安全性和穩定性的應用程式。

2. 高擴展性
   PostgreSQL 支援多種擴展方式，例如可以通過插件系統添加新的功能，也可以自定義資料類型、操作符和函數。

3. 豐富的數據類型
   支援 JSON、XML、地理空間數據（透過 PostGIS 插件）、陣列等複雜數據類型，使得 PostgreSQL 不僅適用於結構化數據，還適合處理半結構化數據。

4. 跨平台
   可以運行在多種操作系統上，例如 Windows、Linux、macOS，因此擁有廣泛的適用性。

5. 大規模應用
   由於其高效能和穩定性，PostgreSQL 被許多大型企業、政府部門和金融機構廣泛採用。

而身為資料庫，<font color=#FF0000>最主要的是由三個結構主成</font>

1. 資料表(table) - 整體資料，包含所有相關資料
2. 欄位(columns) - 定義資料的屬性，和 Data Type
3. 資料列(rows) - 橫向的資料集合，代表一筆完整資料

而資料庫都會與資料庫設計有關，什麼是先? 什麼是後? 這是老師提供非常精美的流程圖

![設計表](/images/table.jpg)

而這時候我們可以探討資料類型的定義(Data Type)的常用類型
![DataType](/images/datatype.jpg)

以目前的學習進度來說，這些常用的類型就綽綽有餘，所以這時候我們就開始學語法

### CREATE TABLE 新增資料表

```
CREATE TABLE user(
	name VARCHAR(20),
  	email VARCHAR(50),
  	age INSERT
);
```

我們先初始化我們想要的資料表，所以建立名稱為 user 的 table

1. 設定欄位名稱為 name，由字元組成，並可容納 20 個字元
2. 設定欄位名稱為 email，由字元組成，並可容納 50 個字元
3. 設定欄位名稱為 age，由數字組成

### INSERT DATA 新增資料內容

建立好資料表之後，就可以來建立資料內容啦
這時我們學到第二個語法，就是插入資料(insert)
<font color=#FF0000>INSERT INTO 資料表名稱</font>
<font color=#FF0000>注意插入類型資料名稱需要使用單引號!，以及程式碼末端需要加 ; 號以示結束</font>

```
//插入單筆資料
insert into users (name,email,age)
VALUES('小菜','123@gmail.com',18)
```

```
//插入多筆資料
insert into users (name,email,age)
VALUES('小菜','123@gmail.com',18),
      ('小華','123222@gmail.com',20),
      ('小麥','122@gmail.com',27);
```

而我想插入資料並不是所有人都會用得到，在大公司的運轉下，大多數的人員都需要查詢功能的能力，這時候我們就介紹 SELECT 查詢功能的語法

### SELECT 查詢

```
-- 查詢所有欄位( * = 查詢所有欄位，顯示所有查詢後的欄位)
-- 選擇 所有欄位 來自於 users的database
SELECT * FROM users;

-- 查詢特定欄位(只要姓名跟年齡)
SELECT name,age FROM users;

```

這裡提供了基本查詢資料表的語法，而另外老師有教很特別的語法(AS 別名)
主要讓資料庫回傳資料時，我們可以用別名做稱，可以更好理解

```
-- 查詢會員資料，設定退休年限資訊
SELECT
    name as 姓名,
    age as 現在年齡,
    65 - age AS 距離退休年紀
    FROM
 users
```

像下圖顯示，我們將資料庫多增加了運算邏輯，真的是有夠方便
![AS](/images/as.jpg)

而這時候我們需要大量的資料去練習，老師也給了 3C 電商網站的範例
![電商商品](/images/3cdatabases.jpg)

### WHERE 篩選

我們的第一個需求，需要找類別是 3C 的產品

```
SELECT name,price FROM products
where category = '3C';
```

找尋結果就會是這樣
![](/images/3ccataglory.jpg)

這時候就會有疑問
<font color=#FF0000>SELECT name,price FROM products</font>代表就是查找資料庫的語法
但對資料庫來說，真正執行順序是什麼呢
這裡老師也有給予解答~~
![](/images/SQLoperation.jpg)

發現原來執行的順序是

1. 搜尋資料表
2. 設定篩選條件 where
3. select 欄位名稱搜尋

資料庫的執行順序並不是我們所輸入的語法順序而定

這時候回到篩選語法 where，我們除了篩選名稱之外，也可以透過比較運算子，去篩選出價格的區間，我們可以透過情境題去練習

情境 1:想知道那些商品快沒貨了，有沒有庫存小於 50 的商品

```
SELECT name, stock
FROM products
WHERE stock <50;
```

情境 2:想知道已經"上架"的"3C"產品
使用 AND = 左右條件都符合 OR 左右條件之一符合

```
SELECT name,price,stock
FROM products
WHERE status ='active'
AND category ='3C';
```

情境 3: 想幫家人買禮物，預算在 500~1000 元

```
SELECT *
FROM products
WHERE discount_price BETWEEN 500 AND 1000;
```

情境 4: 想找出特定商品

```
SELECT *
FROM products
WHERE category IN ('3C','配件') --在category尋找3C跟配件的類別
```

情境 5: 想要排出商品(充電線、手機殼)

```
SELECT *
FROM products
WHERE name NOT IN ('充電線','手機殼') --在category尋找3C跟配件的類別
```

我們一般日常用到新增/查詢，自然也會有 UPDATE(更新)跟 DELETE(刪除)語法

### UPDATE 更新欄位

一樣我們直接用情境來練習
情境 1:調整特定商品價格

```
--更改IPHONE16的價格為28000
UPDATE products
SET price =28000
WHERE name = 'iPhone 16'

--更改多樣欄位
UPDATE products
SET price =28000,
    name = 'iPhone 16 PLUS'
WHERE name = 'iPhone 16'
```

情境 2:更新庫存:增加數量

```
UPDATE products
SET stock = stock + 50
WHERE name = '充電線';
```

### DELETE 刪除欄位

情境 1: 單筆刪除:刪除特定商品

```
DELETE FROM products
WHERE name = 'iPhone 15';

```

情境 2: 條件刪除:刪除類別為 3C 的產品

```
DELETE FROM products
WHERE category = '3C';
```

情境 3: 條件刪除:多重條件刪除:刪除沒庫存且已下架的商品
我們可以先調整庫存

```
--調整庫存
update products
set
	stock = 0,
    status ='inactive'
WHERE name = '手機殼';

--刪除沒庫存且已下架的商品
DELETE FROM products
WHERE stock = 0 AND status ='inactive';
```

---

# 接下來，校長總共出了 15 道題目，讓我們依序來解題

## 模擬資料

![模擬資料](/images/goods.jpg)

如果考量有沒有上下架，程式碼會變得很冗長，故先忽略產品的 status 狀態，active or inactive 因素

#### 情境 1：單品查詢

客人：「這張北歐風雙人沙發多少錢？」
小美想查：想找到這張沙發的價格和庫存

這時候要釐清小美的需求: 1.名字為北歐風雙人沙發 2.價格 3.庫存
所以我需要顯示此三個欄位，故為 SELECT <font color=#FF0000>name , price , stock</font>
而篩選的條件就是名字為<font color=#FF0000>北歐風雙人沙發</font>

```
SELECT name , price, stock FROM goods
WHERE name = '北歐風雙人沙發';
```

#### 情境 2：單品查詢

客人：「請列出 5000 元以下的櫃子有哪些？」
小美想查：找出櫃子類且價格在 5000 以下的商品

第一步要先釐清需求，我們需要 1.低於 5000 2.種類為櫃子的商品
我們需要從所有商品開始查找，所以為 SELECT \* FROM goods 開始
篩選條件為種類是櫃子和價格需要低於 5000 去設定

```
SELECT * FROM goods
WHERE category = '櫃子' AND price < 5000;
```

#### 情境 3：庫存確認

客人：「日式雙人床架還有貨嗎？」
小美想查：確認日式雙人床架的庫存狀況

釐清需求:確認日是雙人床價的庫存，所以顯示條件為 name,stock

```
SELECT name,stock FROM goods
WHERE name = '日式雙人床架';
```

#### 邏輯運算 AND：

#### 情境 4：庫存確認

客人：「想找 4 萬以下，而且有現貨的沙發」
小美想查：要同時符合：是沙發、4 萬以下、有庫存

需求為: 同時符合 1. 沙發 2.價格 4 萬以下 3.有庫存
我們使用 AND 同時滿足三個條件，得到的條件是北歐風雙人沙發

```
SELECT * FROM goods
WHERE category = '沙發' AND price <40000 AND stock> 0;
```

### 情境 5：特價且有貨

客人：「沙發有哪些特價且現貨的品項？」
小美想查：要找到沙發類且有特價（原價大於優惠價）且還有庫存的商品

需求為:同時符合 1. 特價(原價大於優惠價) 2. 有庫存的商品的沙發

```
SELECT * FROM goods
WHERE category = '沙發' AND discount_price < price  AND stock > 0;
```

### 邏輯運算 OR：

### 情境 6：多分類查詢

客人：「我要找櫃子或桌子」
小美想查：要找出櫃子類或桌子類的商品

這裡的需求只要櫃子或桌子 所以我們用 OR，兩者之一只藥都有類別都可以顯示

```
SELECT * FROM goods
WHERE category = '桌子'  OR  category = '櫃子'
```

### 情境 7：指定商品

客人：「北歐風雙人沙發和貓抓皮 L 型沙發哪個還有貨？」
小美想查：要找出這兩張特定沙發的庫存狀況

需求: 需要知道此沙發的庫存，所以顯示名稱跟庫存狀態

```
SELECT name,stock FROM goods
WHERE name = '北歐風雙人沙發'  OR  name = '貓抓皮L型沙發'
```

### IN 運算：

### 情境 8：多分類查詢

客人：「客廳的家具有哪些？我要看沙發、櫃子跟桌子」
小美想查：要找出沙發、櫃子和桌子這三種分類的商品

需求:在類別裡有沙發、櫃子和桌子，可以用 IN 去篩選條件

```
SELECT * FROM products
WHERE category IN ('沙發','櫃子','桌子');
```

### 情境 9：特定商品

客人：「電腦辦公椅和餐椅四入組的價格是多少？」
小美想查：要找出這兩款椅子的價格

需求: 找到名字為電腦辦公椅以及餐椅四人組的價格(有庫存最好)

```
SELECT name,price,stock FROM products
WHERE name IN ('電腦辦公椅','餐椅四入組');
```

### BETWEEN：

### 情境 10：特定商品

客人：「想找 10000 到 20000 之間的商品有哪些？」
小美想查：列出這個價格區間的所有商品

需求，使用 BETWEEN 找出價格區間所有的商品

```
SELECT * FROM products
WHERE price BETWEEN 10000 AND 20000;
```

### 情境 11：庫存區間

主管：「請列出庫存在 5 到 15 之間的商品」
小美想查：列出庫存數量在這個範圍的商品

呈上提，裡用 BETWEEN 做區間篩選

```
SELECT * FROM products
WHERE stock BETWEEN 5 AND 15;
```

### NOT IN：

### 情境 12：排除商品

主管：「列出除了沙發和床架以外的商品」
小美想查：要找出不是沙發和床架的商品

需求: 這裡使用排除，所以用 NOT IN，記得篩選的主要條件改為 category

```
SELECT * FROM products
WHERE category NOT IN ('沙發','床架');
```

### 更新和刪除：

### 情境 13：調整價格

主管：「北歐風雙人沙發要調降 2000 元」
小美想查：要如何更新這張沙發的價格

需求: 將特定物件價格調降 2000
這裡要注意，使用 UPDATE DATABASE
然後 set price = price -2000 (我不知道原始價格多少，但我知道要調降 2000)

再使用 SELECT \* FROM 　 goods 發現北歐風雙人沙發由 39900 => 37900

```
UPDATE goods
SET price =price -2000
WHERE name = '北歐風雙人沙發';
```

### 情境 14：更新庫存

主管：「電腦辦公椅進了 5 張」
小美想查：要如何增加這款椅子的庫存數量

需求: 將特定款的庫存增加，一樣如同上方的題目，我用 stock = stock + 5 增加庫存
庫存將由 20=>25

```
UPDATE goods
SET stock = stock +5
WHERE name = '電腦辦公椅';
```

### 情境 15：清除資料

主管：「要清掉兒童床架和電競書桌的資料」
小美想查：要如何刪除這兩項商品

需求:刪掉特定產品，是兩者皆要刪除 所以可以使用 OR，也可以使用 IN

```
DELETE FROM goods;
WHERE name = '兒童床架' OR name = '電競書桌';

或使用IN
DELETE FROM goods;
WHERE name IN = ('兒童床架,'電競書桌');

```
