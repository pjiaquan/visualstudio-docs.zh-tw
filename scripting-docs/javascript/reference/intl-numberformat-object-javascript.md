---
title: "Intl.NumberFormat 物件 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "NumberFormat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 820bc90f-f1e7-457a-b90d-487dfc3a736d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Intl.NumberFormat 物件 (JavaScript)
提供地區設定特定數字格式。  
  
## 語法  
  
```  
numberFormatObj = new Intl.NumberFormat([locales][, options])  
```  
  
#### 參數  
 `numberFormatObj`  
 必要項。  要指派`NumberFormat`物件的變數名稱。  
  
 `locales`  
 選擇項。  包含一或多個語言或地區設定標記的地區設定字串的陣列。  如果包含多個地區設定的字串，以優先權的遞減順序列出這些字串，使第一個項目是慣用的地區設定。  如果省略這個參數，則會使用 JavaScript 執行階段的預設地區設定。  如需詳細資訊，請參閱「備註」一節。  
  
 `options`  
 選擇項。  包含一個或多個指定數字格式化選項之屬性的物件。  如需詳細資訊，請參閱＜備註＞一節。  
  
## 備註  
 `locales` 參數必須符合 [BCP 47](http://tools.ietf.org/html/rfc5646) 語言或地區設定標記，例如「en\-US」和「zh\-CN」。  標記可能包括語言、國家\/地區和變化。  如需語言標記的範例，請參閱 BCP 47 的[附錄 A](http://tools.ietf.org/html/rfc5646#appendix-A) \(英文\)。  對於 `NumberFormat`，您可能加入後面接著 \-nu 的 **\-u** 子標記以指定編號系統延伸：  
  
 "*language*\-*region*\-u\-nu\-*numberingsystem*"  
  
 其中 *numberingsystem* 可以是下列其中一項：arab, arabext, bali, beng, deva, fullwide, gujr, guru, hanidec, khmr, knda, laoo, latn, limb, mylm, mong, mymr, orya, tamldec, telu, thai, tibt。  
  
 `options` 參數可能包含下列屬性：  
  
|屬性|描述|可能的值|預設值|  
|--------|--------|----------|---------|  
|`localeMatcher`|指定要使用的地區設定比對演算法。|"查詢", "自動調整"|"自動調整"|  
|`style`|指定編號格式樣式。|"十進位", "百分比", "貨幣"|"decimal"|  
|`currency`|指定 ISO 4217 貨幣值為字母代碼。  如果 `style` 是設定為 "currency"，則這個值為必要項。|請參閱 ISO [貨幣和基金代碼清單](http://www.currency-iso.org/en/home/tables/table-a1.html) \(英文\)。|未定義|  
|`currencyDisplay`|指定貨幣顯示為 ISO 4217 字母貨幣代碼、當地語系化貨幣符號或當地語系化貨幣名稱。  這個值只在 `style` 設定為 "currency" 時使用。|"程式碼", "符號", "名稱"|"symbol"|  
|`useGrouping`|指定是否應該使用群組分隔符號。|true、false|`true`.|  
|`minimumIntegerDigits`|指定要使用的整數位數下限。|1 至 21。|21|  
|`minimumFractionDigits`|.  指定要使用的小數位數下限。|0 至 20。|0|  
|`maximumFractionDigits`|指定要使用的小數位數上限。|這個值的範圍可從 `minimumFractionDigits` 到 20。|20.|  
|`minimumSignificantDigits`|指定要顯示的小數位數下限。|這個值的範圍可從 1 到 21。|1|  
|`maximumSignificantDigits`|指定要顯示的小數位數上限。|這個值的範圍可從 `minimumSignificantDigits` 到 21。|21|  
  
## 屬性  
 下表列出 `NumberFormat` 物件的屬性。  
  
|||  
|-|-|  
|屬性|描述|  
|[建構函式](../../javascript/reference/constructor-property-intl-numberformat.md)|指定用來建立數字格式子物件的函式。|  
|[format](../../javascript/reference/format-property-intl-numberformat.md)|傳回函式，透過使用數字格式子設定，格式化數字。|  
|[Prototype \- 原型](../../javascript/reference/prototype-property-intl-numberformat.md)|傳回數字格式子的原型參考。|  
  
## 方法  
 下表列出 `NumberFormat` 物件的方法。  
  
|||  
|-|-|  
|方法|描述|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-numberformat.md)|傳回物件，其中包含數字格式子物件的屬性和值。|  
  
## 範例  
 下列範例會使用指定的格式化選項，建立 en\-US 地區設定的 `NumberFormat` 物件。  
  
```javascript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
});  
  
if (console && console.log) {  
    console.log(nf.format(100)); // Returns ¥100.00  
}  
```  
  
## 範例  
 下列範例顯示使用數個不同地區設定和選項的結果。  
  
```javascript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
if (console && console.log) {  
    console.log(new Intl.NumberFormat("en-US").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ja-JP").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ar-SA", options1).format(number));  
    // Returns ١٢,٣٤٥,٦٧٨,٩٠٠ %  
    console.log(new Intl.NumberFormat("hi-IN", options2).format(number));  
    // Returns ₹ 12,34,56,789.00  
}  
```  
  
## 需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 請參閱  
 [toLocaleString \(數字\)](../../javascript/reference/tolocalestring-number.md)   
 [Intl.Collator 物件](../../javascript/reference/intl-collator-object-javascript.md)   
 [Intl.DateTimeFormat 物件](../../javascript/reference/intl-datetimeformat-object-javascript.md)