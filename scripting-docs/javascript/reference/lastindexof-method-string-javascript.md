---
title: "lastIndexOf 方法 (字串) (JavaScript) | Microsoft Docs"
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
  - "lastIndexOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lastIndexOf 方法，字串"
  - "字串，lastIndexOf 方法"
ms.assetid: 1ed36ccd-0f0b-4f16-be45-0567207670af
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# lastIndexOf 方法 (字串) (JavaScript)
傳回子字串最後出現在字串中的位置。  
  
## 語法  
  
```  
  
strObj.lastIndexOf(substring[, startindex])  
```  
  
## 參數  
 `strObj`  
 必要項。  `String` 物件或字串常值。  
  
 `substring`  
 必要項。  要搜尋的子字串。  
  
 `startindex`  
 選擇項。  要開始搜尋的索引。  若予以省略，則會從字串的結尾開始搜尋。  
  
## 備註  
 **lastIndexOf** 方法會傳回整數值，表示子字串的開頭在 `String` 物件中的位置。  如果找不到子字串，則傳回 \-1。  
  
 如果 `startindex` 是負數，則 `startindex` 會被視為零。  如果此值大於字元位置索引上限，則會將其視為該上限值。  
  
 搜尋是從字串中的最後一個字元開始執行。  否則這方法就與 **indexOf** 相同。  
  
 以下範例說明如何使用 **lastIndexOf** 方法。  
  
```javascript  
var str = "time, time";  
  
var s = "";  
s += "time is at position " + str.lastIndexOf("time");  
s += "<br />";  
s += "abc is at position " + str.lastIndexOf("abc");  
  
document.write(s);  
  
// Output:  
// time is at position 6  
// abc is at position -1  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[String 物件](../../javascript/reference/string-object-javascript.md)  
  
## 請參閱  
 [indexOf 方法 \(字串\)](../../javascript/reference/indexof-method-string-javascript.md)