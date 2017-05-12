---
title: "compare 屬性 (Intl.Collator) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 59f274dc-6e52-4344-8d5c-b9f0000b66e0
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# compare 屬性 (Intl.Collator)
傳回函式，透過使用自動分頁器的排序次序比較兩個字串。  
  
## 語法  
  
```javascript  
collatorObj.compare  
```  
  
#### 參數  
 `collatorObj`  
 必要項。  比較所用之 `Collator` 物件的名稱。  
  
## 備註  
 `compare` 屬性傳回的函式採用兩個引數 `x` 和 `y`，並使用 `Collator` 物件指定的選項，傳回 `x` 和 `y` 地區設定特定比較的結果。  
  
 比較的結果會是：  
  
-   如果 `x` 的排序次序在 `y` 之前，則為 \-1。  
  
-   如果 `x` 的排序次序中等於 `y`，則為 0 \(零\)。  
  
-   如果 `x` 的排序次序在 `y` 之後，則為 1。  
  
## 範例  
 在下列範例中會建立 `Collator` 物件，並執行比較。  
  
```javascript  
var co = new Intl.Collator(["de-DE-u-co-phonebk"]);  
  
if (console && console.log) {  
    console.log(co.compare("a", "b")); // Returns -1  
}  
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
 下列範例使用 `Collator` 物件來搜尋字串。  
  
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
 [Intl.Collator 物件](../../javascript/reference/intl-collator-object-javascript.md)