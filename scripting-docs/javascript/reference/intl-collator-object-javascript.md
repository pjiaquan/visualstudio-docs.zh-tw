---
title: "Intl.Collator 物件 (JavaScript) | Microsoft Docs"
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
  - "Collator"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: acbb9461-f956-4b5b-ae5f-6a47815ae15c
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Intl.Collator 物件 (JavaScript)
提供地區設定特定的字串比較。  
  
## 語法  
  
```  
collatorObj = new Intl.Collator([locales][, options])  
```  
  
#### 參數  
 `collatorObj`  
 必要項。  要指派`Collator`物件的變數名稱。  
  
 `locales`  
 選擇項。  包含一或多個語言或地區設定標記的地區設定字串的陣列。  如果包含多個地區設定的字串，以優先權的遞減順序列出這些字串，使第一個項目是慣用的地區設定。  如果省略這個參數，則會使用 JavaScript 執行階段的預設地區設定。  如需詳細資訊，請參閱「備註」一節。  
  
 `options`  
 選擇項。  包含一個或多個指定比較選項之屬性的物件。  如需詳細資訊，請參閱＜備註＞一節。  
  
## 備註  
 `locales` 參數必須符合 [BCP 47](http://tools.ietf.org/html/rfc5646) 語言或地區設定標記，例如「en\-US」和「zh\-Hans\-CN」。  標記可能包括語言、國家\/地區和變化。  如需語言清單，請參閱 [IANA 語言子標記登錄](http://go.microsoft.com/fwlink/p/?linkid=227303) \(英文\)。  如需語言標記的範例，請參閱 BCP 47 的[附錄 A](http://tools.ietf.org/html/rfc5646#appendix-A) \(英文\)。  對於 `Collator`，您可以在地區設定字串中包含 \-u 延伸以指定下列其中一個或多個 Unicode 延伸：  
  
-   \-co 可以指定不同的定序 \(地區設定專用\)："*language*\-*region*\-u\-co\-*value*"。  
  
-   \-kn 用來指定數值比較："*language*\-*region*\-u\-kn\-true&#124;false"。  
  
-   –kf 用來指定要先排序大寫或小寫字元："*language*\-*region*\-u\-kf\-upper&#124;lower&#124;false"\)。  目前不支援這副檔名。  
  
 若要指定數值比較，您可以在地區設定的字串中設定 – kn 擴充功能，或使用 `options` 參數中的 `numeric` 屬性。  如果您使用 `numeric` 屬性，則 –kn 值不適用。  
  
 `options` 參數可能包含下列屬性：  
  
-   `localeMatcher`.  指定要使用的地區設定比對演算法。  可能值為 "lookup" 和 "best fit"。  預設值為 \[自動調整\]。  
  
-   `usage`.  指定比較目標是排序或搜尋。  可能的值為 "sort" 和 "search"。  預設值為 \[排序\]。  
  
-   `sensitivity`.  指定自動分頁器的敏感度。  可能的值為 "base"、"accent"、"case" 和 "variant"。  預設值是 `undefined`。  
  
-   `ignorePunctuation`.  指定是否在比較中忽略標點符號。  可能的值為 "true" 和 "false"。  預設值是 `false`。  
  
-   `numeric`.  指定是否使用數字排序。  可能的值為 "true" 和 "false"。  預設值是 `false`。  
  
-   `caseFirst`.  目前尚不支援。  
  
## 屬性  
 下表列出 `Collator` 物件的屬性。  
  
|||  
|-|-|  
|屬性|描述|  
|[compare](../../javascript/reference/compare-property-intl-collator.md)|傳回函式，透過使用自動分頁器的排序次序比較兩個字串。|  
|[建構函式](../../javascript/reference/constructor-property-intl-collator.md)|指定建立自動分頁器的函式。|  
|[Prototype \- 原型](../../javascript/reference/prototype-property-intl-collator.md)|傳回自動分頁器的原型參考。|  
  
## 方法  
 下表列出 `Collator` 物件的方法。  
  
|||  
|-|-|  
|方法|描述|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-collator.md)|傳回物件，其中包含自動分頁器的屬性和值。|  
  
## 範例  
 在下列範例中會建立 `Collator` 物件，並執行比較。  
  
```javascript  
var co = new Intl.Collator(["de-DE"]);  
co.compare("a", "b"); // Returns -1  
  
```  
  
## 範例  
 下列範例使用 `Collator` 物件來排序陣列。  這個範例示範地區設定特定的差異。  
  
```javascript  
var co1 = new Intl.Collator(["de-DE-u-co-phonebk"]);  
var co2 = new Intl.Collator(["de-DE"]);  
var co3 = new Intl.Collator(["en-US"]);  
  
var arr = ["ä", "ad", "af", "a"];  
  
if (console && console.log) {  
    console.log(arr.sort(co1.compare));  // Returns a,ad,ä,af  
    console.log(arr.sort(co2.compare));  // Returns a,ä,ad,af  
    console.log(arr.sort(co3.compare));  // Returns a,ä,ad,af  
}  
```  
  
## 範例  
 下列範例會使用 `Collator` 物件來搜尋字串和指定比較選項。  
  
```javascript  
// String to search  
var arr = ["ä", "ad", "af", "a"];  
// String searched for  
var s = "af";  
  
var co = new Intl.Collator("de-DE", { usage: "search" });  
var matches = arr.filter(function (i) {  
    return co.compare(i, s) === 0;  
});  
  
if (console && console.log) {  
    console.log(matches);  // Returns af  
}  
```  
  
## 需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 請參閱  
 [localeCompare 方法 \(字串\)](../../javascript/reference/localecompare-method-string-javascript.md)   
 [Intl.DateTimeFormat 物件](../../javascript/reference/intl-datetimeformat-object-javascript.md)   
 [Intl.NumberFormat 物件](../../javascript/reference/intl-numberformat-object-javascript.md)