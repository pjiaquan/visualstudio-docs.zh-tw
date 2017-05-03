---
title: "for...in 陳述式 (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "反覆運算陳述式, for...in 陳述式"
  - "迴圈結構, for...in 陳述式"
ms.assetid: 1b51a0ce-89f7-4a69-88ed-017b47dc398f
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# for...in 陳述式 (JavaScript)
針對物件的每個屬性或陣列的每個元素，執行一個或多個陳述式。  
  
## 語法  
  
```  
for (variable in [object | array]) {  
    statements   
}  
```  
  
## 參數  
 `variable`  
 必要項。  variable 可以是 `object` 的任何屬性名稱或 `array` 的任何元素索引。  
  
 `object`, `array`  
 選擇項。  要重複執行的目標物件或陣列。  
  
 `statements`  
 選擇項。  要針對 `object` 的每個屬性或 `array` 的每個元素執行的一個或多個陳述式。  可以是複合陳述式。  
  
## 備註  
 每次迴圈開始執行時，`variable` 的值就是 `object` 的下一個屬性值或 `array` 的下一個元素索引。  接著，您就可以在迴圈內的任何陳述式中使用 `variable` 來參考 `object` 的屬性或 `array` 的元素。  
  
 執行迴圈時，我們並不會知道每一次指派的是物件的哪個屬性，  因此您無法依迴圈的索引指定特定屬性，只能依屬性的名稱來指定。  
  
 針對陣列執行迴圈時，是依照元素的順序 \(也就是 0、1、2\) 來執行。  
  
## 範例  
 以下範例說明 `for...in` 陳述式和做為關聯陣列的物件搭配使用的方法。  
  
```javascript  
// Initialize object.  
a = {"a" : "Athens" , "b" : "Belgrade", "c" : "Cairo"}  
  
// Iterate over the properties.  
var s = ""  
for (var key in a) {  
    s += key + ": " + a[key];  
    s += "<br />";  
    }  
document.write (s);  
  
// Output:  
// a: Athens  
// b: Belgrade  
// c: Cairo  
```  
  
## 範例  
 以下範例說明如何使用 `for ... in` 陳述式來重複執行含有 expando 屬性的 `Array` 物件。  
  
```javascript  
// Initialize the array.  
var arr = new Array("zero","one","two");  
  
// Add a few expando properties to the array.  
arr["orange"] = "fruit";  
arr["carrot"] = "vegetable";  
  
// Iterate over the properties and elements.  
var s = "";  
for (var key in arr) {  
    s += key + ": " + arr[key];  
    s += "<br />";  
}  
  
document.write (s);  
  
// Output:  
//   0: zero  
//   1: one  
//   2: two  
//   orange: fruit  
//   carrot: vegetable  
```  
  
> [!NOTE]
>  請使用 `Enumerator` 物件反覆查看集合的成員。  
  
## 需求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## 請參閱  
 [for 陳述式](../../javascript/reference/for-statement-javascript.md)   
 [while 陳述式](../../javascript/reference/while-statement-javascript.md)