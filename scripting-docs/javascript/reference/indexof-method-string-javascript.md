---
title: "indexOf 方法 (字串) (JavaScript) | Microsoft Docs"
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
  - "indexOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "indexOf 方法, 字串"
  - "字串, indexOf 方法"
ms.assetid: a17372fa-669b-471b-9240-46927a265152
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# indexOf 方法 (字串) (JavaScript)
傳回子字串第一個出現的位置。  
  
## 語法  
  
```  
  
strObj. indexOf(subString[, startIndex])  
```  
  
## 參數  
 `strObj`  
 必要項。  `String` 物件或字串常值。  
  
 `subString`  
 必要項。  要在字串中搜尋的子字串  
  
 `startIndex`  
 選擇項。  要開始搜尋 `String` 物件的索引位置。  如果省略，則會從字串的開頭開始搜尋。  
  
## 備註  
 **indexOf** 方法會傳回 `String` 物件中子字串的開頭。  如果找不到子字串，則傳回 \-1。  
  
 如果 `startindex` 是負數，則會將 `startindex` 視為零。  如果大於最高的索引，則會將其視為最高的索引。  
  
 搜尋是由左至右進行。  否則這個方法就與 **lastIndexOf** 完全相同。  
  
## 範例  
 以下範例將示範如何使用 **indexOf** 方法。  
  
```javascript  
var str = "original equipment manufacturer";  
  
var s = "equip is at position " + str.indexOf("equip");  
s += "<br />";  
s += "abc is at position " + str.indexOf("abc");  
  
document.write(s);  
  
// Output:  
// equip is at position 9  
// abc is at position -1  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[String 物件](../../javascript/reference/string-object-javascript.md)  
  
## 請參閱  
 [lastIndexOf 方法 \(字串\)](../../javascript/reference/lastindexof-method-string-javascript.md)   
 [捲動、移動瀏覽和縮放範例應用程式](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)