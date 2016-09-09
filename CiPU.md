# CiPU 喜舖 GTM代碼設定說明

# Version
>20160907

# 文件目錄 

[TOC]

<br><br>
# 追蹤代碼簡介

為協助廣告主有效分析瀏覽者進入站內購物行為事件，須請客戶協助在全站網頁埋入Google Tag Manager代碼(簡稱GTM)，並在`目錄頁`、`商品頁`、`購物車頁`、`結帳完成頁`埋入產品資訊參數，以便GTM取得數值並傳至報表系統。

頁面說明：

>* 首頁
* 目錄頁 - 商品分類，商品列表
* 商品頁 - 商品資訊頁面
* 購物車頁 - 加入購物車的頁面
* 結帳完成頁 - 最後結帳完成的頁面

<br>
接下來將詳細描述埋入GTM代碼與產品相關參數。

<br><br>
# GTM 代碼
**說明**
>
GTM為全站統一使用之程式碼，請埋於全站網頁中，置於`</body>`之前。

**程式碼**

```javascript
<!-- Google Tag Manager -->
<noscript><iframe src="//www.googletagmanager.com/ns.html?id=GTM-XXXXXX"
height="0" width="0" style="display:none;visibility:hidden"></iframe></noscript>
<script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
'//www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
})(window,document,'script','dataLayer','GTM-56H352');</script>
<!-- End Google Tag Manager -->
```

<br><br>
# GTM 產品資訊參數
**說明**
>
各瀏覽產品事件所需之參數，請埋於對應之頁面並置於GTM代碼之前。

## 目錄頁
**說明**
>
>
請將程式碼埋入網站各目錄頁，包括Desktop與Mobile版本，例如：<br>
https://www.cipu.com.tw/category.php?ph1=1&ruc=27<br>

**參數 (＊必填)**

參數            | 型態|說明     | 範例
---------------|------|---|-------------------------
`product_type`＊    | 字串|頁面類型 | 首頁 > CiPU Bag
`mhash` |字串| 會員登入email hash，用於跨螢識別<br>PHP語法範例：hash("sha256","mary@example.com")| f1904cf1a9d73a55fa5de0ac823c4403ded71afd4c3248d00bdcd0866552bb79


**程式碼**

```javascript
<script type="text/javascript">
	var product = {
		product_type : '首頁 > CiPU Bag',
		mhash : 'f1904cf1a9d73a55fa5de0ac823c4403ded71afd4c3248d00bdcd0866552bb79',
	};
</script>

```

## 商品頁
**說明**
>
請將程式碼埋入網站各產品頁，包括Desktop與Mobile版本，例如：<br>
https://www.cipu.com.tw/product.php?pd=HB&pc=NA&ps=091

**參數 (＊必填)**

參數            | 型態|說明     | 範例
---------------|------|---|-------------------------
`id`＊    | 字串|產品ID | P0005800047157
`product_type`＊    | 字串|商品類別 | 首頁 > CiPU Bag > Accessory
`title`＊|字串|產品名稱|隨意手拿包(馬賽克)
`description`|字串|商品描述|可擺放存摺、手機、悠遊卡等物品<br>當作相機包使用也相當適合<br>防潑水材質,更耐髒<br>小包內有夾層分隔,私人物品都可以擺放整齊
`brand`|字串|品牌名稱|CiPU喜舖
`sale_price`＊|數值|售價|449
`price`|數值|定價|449
`currency`＊|字串|幣別|TWD
`link`＊|字串|網址|https://www.cipu.com.tw/product.php?pd=HB&pc=NA&ps=091
`image_link`＊|字串|產品圖網址|http://media.cipu.com.tw//media/images/2.0%20product/shop%20123/540/FT-N2-03.jpg
`mhash` |字串| 會員登入email hash，用於跨螢識別<br>PHP語法範例：hash("sha256","mary@example.com")| f1904cf1a9d73a55fa5de0ac823c4403ded71afd4c3248d00bdcd0866552bb79

**程式碼**
		
```javascript
<script type="text/javascript">
	var product = {
		id : 'P0005800047157',
		product_type : '首頁 > CiPU Bag > Accessory',
		title :'隨意手拿包(馬賽克)',
		description : '可擺放存摺、手機、悠遊卡等物品,當作相機包使用也相當適合,防潑水材質,更耐髒,小包內有夾層分隔,私人物品都可以擺放整齊',
		brand : 'CiPU喜舖',
		sale_price : 449,
		price : 449,
		currency : 'TWD',
		link : 'https://www.cipu.com.tw/product.php?pd=HB&pc=NA&ps=091',
		image_link : 'http://media.cipu.com.tw//media/images/2.0%20product/shop%20123/540/FT-N2-03.jpg',
		mhash : 'f1904cf1a9d73a55fa5de0ac823c4403ded71afd4c3248d00bdcd0866552bb79'
	}; 
</script>
```



## 購物車頁
**說明**
>
請將程式碼埋入網站購物車頁，包括Desktop與Mobile版本，例如：<br>
https://www.cipu.com.tw/shoppingcart.php

**參數 (＊必填)**

參數            | 型態|說明     | 範例
---------------|------|---|-------------------------
`order_price`|數值 |訂單金額：為商品總額並結算運費或折扣後的費用|1478
`products`＊|陣列|購物清單，每筆商品陣列由以下組成<br>貨號：`id` <br>產品名稱：`title`<br>售價：`sale_price`<br>單品總價：`total`<br>幣別：`currency`<br>數量：`quantity`|{ id : 'P0005800047157' , title : '隨意手拿包' , sale\_price : 449 , total : 898 , currency : 'TWD' , quantity : 2}<br>{ id : 'P0029200021313' , title : '搖滾阿珠馬' , sale\_price : 580 , total : 580 , currency : 'TWD' , quantity : 1}
`mhash` |字串| 會員登入email hash，用於跨螢識別<br>PHP語法範例：hash("sha256","mary@example.com")| f1904cf1a9d73a55fa5de0ac823c4403ded71afd4c3248d00bdcd0866552bb79


**程式碼**		

```javascript
<script type="text/javascript">
	var basket = {
		order_price : 1478,
		products : [
			{ id : 'P0005800047157' , title : '隨意手拿包', sale_price : 449 , total : 898 , currency : 'TWD' , quantity : 2 },
			{ id : 'P0029200021313' , title : '搖滾阿珠馬', sale_price : 580 , total : 580 , currency : 'TWD' , quantity : 1 }
		],
		mhash : 'f1904cf1a9d73a55fa5de0ac823c4403ded71afd4c3248d00bdcd0866552bb79'
 		};
</script>
```





## 結帳完成頁
**說明**
>
請將程式碼埋入結帳完成頁，包括Desktop與Mobile版本，例如：<br>
https://www.cipu.com.tw/orderpay_webatm.php

**參數 (＊必填)**

參數            | 型態|說明     | 範例
---------------|------|---|-------------------------
`order_id`|字串|訂單編號|500020604
`order_price`|數值 |訂單金額：為商品總額並結算運費或折扣後的費用|1478
`currency`|字串|幣別|TWD
`products`＊|陣列|購物清單，每筆商品陣列由以下組成<br>貨號：`id` <br>產品名稱：`title`<br>售價：`sale_price`<br>單品總價：`total`<br>幣別：`currency`<br>數量：`quantity`|{ id : 'P0005800047157' , title : '隨意手拿包' , sale\_price : 449 , total : 898 , currency : 'TWD' , quantity : 2}<br>{ id : 'P0029200021313' , title : '搖滾阿珠馬' , sale\_price : 580 , total : 580 , currency : 'TWD' , quantity : 1}
`mhash` |字串| 會員登入email hash，用於跨螢識別<br>PHP語法範例：hash("sha256","mary@example.com")| f1904cf1a9d73a55fa5de0ac823c4403ded71afd4c3248d00bdcd0866552bb79

**程式碼**

```javascript
<script type="text/javascript">
	var basket = {
		order_id : '500020604',
		order_price : 1478,
		currency : 'TWD',
		products : [
			{ id : 'P0005800047157' , title : '隨意手拿包', sale_price : 449 , total : 898 , currency : 'TWD' , quantity : 2 },
			{ id : 'P0029200021313' , title : '搖滾阿珠馬', sale_price : 580 , total : 580 , currency : 'TWD' , quantity : 1 }
		],
       mhash :'f1904cf1a9d73a55fa5de0ac823c4403ded71afd4c3248d00bdcd0866552bb79'
	};
</script>
```
