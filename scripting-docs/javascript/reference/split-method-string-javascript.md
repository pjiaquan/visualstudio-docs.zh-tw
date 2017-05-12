---
title: "split 方法 (字串) (JavaScript) | Microsoft Docs"
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
  - "split"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "split 方法"
ms.assetid: 7f093336-c887-4efb-b91f-819b6d18a181
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# split 方法 (字串) (JavaScript)
使用指定的分隔符號將字串分割成子字串，並以陣列方式傳回子字串。  
  
## 語法  
  
```  
  
stringObj.split([separator[, limit]])  
```  
  
## 參數  
 `stringObj`  
 必要項。  要分割的 `String` 物件或字串常值。  **split** 方法不會修改這個物件。  
  
 `separator`  
 選擇項。  字串或**規則運算式**物件，可識別用來分隔字串的一個或多個字元。  如果省略，則會傳回包含整個字串的單一元素陣列。  
  
 `limit`  
 選擇項。  用來限制陣列中所傳回元素個數的值。  
  
## 傳回值  
 **split** 方法的結果是字串陣列，其分割位置為 `stringObj` 內出現 `separator` 的每個點。  `separator` 並不會包含在傳回的任何陣列元素中。  
  
## 範例  
 以下範例將說明如何使用 **split** 方法。  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.split(" ");  
for (var i in ss) {  
    document.write(ss[i]);  
    document.write("<br/>");  
}  
  
// Output:   
// The  
// quick  
// brown  
// fox  
// jumps  
// over  
// the  
// lazy  
// dog.  
  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[String 物件](../../javascript/reference/string-object-javascript.md)  
  
## 請參閱  
 [concat 方法 \(字串\)](../../javascript/reference/concat-method-string-javascript.md)   
 [RegExp 物件](../../javascript/reference/regexp-object-javascript.md)   
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-tw/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [捲動、移動瀏覽和縮放範例應用程式](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)