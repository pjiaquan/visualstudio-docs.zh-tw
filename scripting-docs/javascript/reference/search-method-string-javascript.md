---
title: "search 方法 (字串) (JavaScript) | Microsoft Docs"
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
  - "search"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "search 方法"
ms.assetid: 1cae0fbc-3319-4327-ba4e-d5fa2c4a9ba0
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# search 方法 (字串) (JavaScript)
尋找規則運算式搜尋中第一個符合的子字串。  
  
## 語法  
  
```  
  
stringObj.search(rgExp)   
```  
  
## 參數  
 `stringObj`  
 必要項。  要執行搜尋的目標 `String` 物件或字串常值。  
  
 `rgExp`  
 必要項。  包含規則運算式模式和適用旗標之**規則運算式**物件的執行個體。  
  
## 傳回值  
 如果找到符合的項目，**search** 方法會傳回整數值，表示從第一個符合字串起算的位移；  如果找不到符合項目，則會傳回 \-1。  
  
## 備註  
 您也可以設定 `i` 旗標，讓搜尋不區分大小寫。  
  
## 範例  
 以下範例說明如何使用 **search** 方法。  
  
```javascript  
var src = "is but a Dream within a dream";  
var re = /dream/;  
var pos = src.search(re);  
document.write(pos);  
document.write("<br/>");  
  
re = /dream/i;  
pos = src.search(re);  
document.write(pos);  
  
// Output:   
// 24   
// 9  
  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[String 物件](../../javascript/reference/string-object-javascript.md)  
  
## 請參閱  
 [exec 方法 \(規則運算式\)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [match 方法 \(字串\)](../../javascript/reference/match-method-string-javascript.md)   
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-tw/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [replace 方法 \(字串\)](../../javascript/reference/replace-method-string-javascript.md)   
 [test 方法 \(規則運算式\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/zh-tw/3b62e27c-4f07-4726-a95b-6e841807bfaf)