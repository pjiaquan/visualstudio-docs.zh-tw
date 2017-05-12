---
title: "concat 方法 (字串) (JavaScript) | Microsoft Docs"
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
  - "concat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "concat 方法 (字串)"
  - "Concat 方法"
ms.assetid: 5d28ebb2-d534-4179-9297-a4c821ee9f24
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# concat 方法 (字串) (JavaScript)
傳回字串，此字串會串連兩個或多個字串。  
  
## 語法  
  
```  
  
string1. concat([string2[, string3[, . . . [, stringN]]]])  
```  
  
## 參數  
 `string1`  
 必要項。  串連所有其他指定之字串的 `String` 物件或字串常值。  
  
 `string2,. . ., stringN`  
 選擇項。  要附加至 `string1` 結尾的字串。  
  
## 備註  
 `concat` 方法的結果相當於：`result` \= `string1` \+ `string2` \+ `string3` \+ `stringN`。  無論是原始或結果字串中的值發生改變，都不會彼此影響字串中的值。  如果有任何的引數不是字串，這些引數會先轉換成字串，再串連到 `string1`。  
  
## 範例  
 以下範例說明如何搭配字串使用 `concat` 方法︰  
  
```javascript  
var str1 = "ABCD"  
var str2 = "EFGH";  
var str3 = "1234";  
var str4 = "5678";  
document.write(str1.concat(str2, str3, str4));  
  
// Output: "ABCDEFGH12345678"  
  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[String 物件](../../javascript/reference/string-object-javascript.md)  
  
## 請參閱  
 [加法運算子 \(\+\)](../../javascript/reference/addition-operator-decrement-javascript.md)