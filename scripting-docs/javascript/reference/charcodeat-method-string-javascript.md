---
title: "charCodeAt 方法 (字串) (JavaScript) | Microsoft Docs"
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
  - "charCodeAt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "charCodeAt 方法"
ms.assetid: 5b0290a7-ee4d-4738-a909-c02ef64a2f1a
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# charCodeAt 方法 (字串) (JavaScript)
在指定位置傳回字元的 Unicode 值。  
  
## 語法  
  
```  
  
strObj. charCodeAt(index)  
```  
  
## 參數  
 `strObj`  
 必要項。  任何 `String` 物件或字串常值。  
  
 `index`  
 必要項。  所需字元之以零為起始的索引。  如果指定的索引處沒有任何字元，則傳回 `NaN`。  
  
## 備註  
  
## 範例  
 在下列範例中，說明了如何使用 `charCodeAt` 方法。  
  
```javascript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";   
document.write(str.charCodeAt(str.length - 1));  
  
// Output: 90   
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 請參閱  
 [String.fromCharCode 函式](../../javascript/reference/string-fromcharcode-function-javascript.md)