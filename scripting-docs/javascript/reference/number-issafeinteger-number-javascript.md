---
title: "Number.isSafeInteger (數字) (JavaScript) | Microsoft Docs"
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
ms.assetid: c7ef6ce8-fe71-4e53-be44-4dd440aef21d
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Number.isSafeInteger (數字) (JavaScript)
傳回布林值，表示是否可以在 JavaScript 中安全地表示數字。  
  
## 語法  
  
```  
Number.isSafeInteger(numValue)   
```  
  
## 傳回值  
 如果此數字位於 `Number.MIN_SAFE_INTEGER` 和 `Number.MAX_SAFE_INTEGER` 之間 \(含\) 則為 `true`；否則為 `false`。  
  
## 備註  
 在 JavaScript 中的安全整數是在套用任何進位之前的 IEEE\-754 雙精確度數字。  
  
## 範例  
  
```javascript  
// Returns true  
Number.isSafeInteger(-100)  
Number.isSafeInteger(9007199254740991)  
  
// Returns false  
Number.isSafeInteger(Number.NaN)  
Number.isSafeInteger(Infinity)  
Number.isSafeInteger("100")  
Number.isSafeInteger(9007199254740992);  
```  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **適用於**：[Number 物件](../../javascript/reference/number-object-javascript.md)