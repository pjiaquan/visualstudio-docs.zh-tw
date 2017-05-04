---
title: "substring 方法 (字串) (JavaScript) | Microsoft Docs"
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
  - "substring"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "子字串"
  - "substring 方法"
ms.assetid: 9cf9a005-cbe3-42fd-828b-57a39f54224c
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# substring 方法 (字串) (JavaScript)
傳回 `String` 物件中指定之位置的子字串。  
  
## 語法  
  
```  
  
      strVariable. substring(start [, end])  
"String Literal".substring(start [, end])   
```  
  
## 參數  
 `start`  
 必要項。  以零為起始的索引整數，表示子字串的開頭。  
  
 `end`  
 選擇項。  以零為起始的索引整數，表示子字串的結尾。  此子字串包含的字元一直到 \(但不包括\) `end` 所指定的字元。  
  
 如果省略 `end`，便會傳回從 `start` 一直到原始字串結尾的字元。  
  
## 備註  
 `substring` 方法傳回的字串將包含從 `start` 開始到 `end` 的子字串，但不包含後者本身。  
  
 **substring** 方法會使用 `start` 和 `end` 中較小的值做為子字串的起點。  例如 strvar.substring\(0, 3\) 和 strvar.substring\(3, 0\) 會傳回相同的子字串。  
  
 如果 `start` 或 `end` 中的任何一個是 `NaN` 或負數，其值將會變成 0。  
  
 子字串的長度等於 `start` 和 `end` 二者之間差異的絕對值。  例如，strvar.substring\(0, 3\) 和 strvar.substring\(3, 0\) 中所傳回的子字串長度都是 3。  
  
## 範例  
 以下範例說明如何使用 **substring** 方法。  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substring(10, 15);  
document.write(ss);  
  
// Output:  
// brown  
  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [substr 方法 \(字串\)](../../javascript/reference/substr-method-string-javascript.md)