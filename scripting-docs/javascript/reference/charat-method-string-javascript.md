---
title: "charAt 方法 (String) (JavaScript) | Microsoft Docs"
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
  - "charAt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "字串物件，傳回字元"
  - "charAt 方法"
  - "字元，傳回一部分"
ms.assetid: 63173e15-17f6-47c5-8f94-98ef1eb04c1a
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# charAt 方法 (String) (JavaScript)
傳回位於指定索引的字元。  
  
## 語法  
  
```  
  
strObj. charAt(index)  
```  
  
## 參數  
 `strObj`  
 必要項。  任何 `String` 物件或字串常值。  
  
 `index`  
 必要項。  所需字元之以零為起始的索引。  
  
## 備註  
 `charAt` 方法所傳回的字元值與指定之 `index` 處的字元相同。  字串中第一個字元的索引是 0，第二個字元的索引是 1，依此類推。  落在範圍以外的 `index` 值會傳回空字串。  
  
## 範例  
 在下列範例中，說明了如何使用 `charAt` 方法：  
  
```javascript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";  
document.write(str.charAt(str.length - 1));  
  
// Output: Z  
  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[String 物件](../../javascript/reference/string-object-javascript.md)  
  
## 請參閱  
 [String 物件](../../javascript/reference/string-object-javascript.md)