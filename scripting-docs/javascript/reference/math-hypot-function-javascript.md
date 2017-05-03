---
title: "Math.hypot 函式 (JavaScript) | Microsoft Docs"
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
ms.assetid: 31488f5a-2230-4114-911e-b6d854c7b0a0
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Math.hypot 函式 (JavaScript)
傳回引數平方總和的平方根。  
  
## 語法  
  
```  
Math.hypot ( value1[, value2[, ...values] );  
```  
  
#### 參數  
 `value1`  
 必要項。  第一個數字。  
  
 `value2`  
 選擇項。  第二個數字。  
  
 `values`  
 選擇項。  一個或多個數字。  
  
## 備註  
 如果有任何引數是 NaN，則函式會傳回 NaN。  如果未提供任何引數，則函式會傳回 0。  
  
## 範例  
 下列範例示範使用 `Math.hypot` 函式的範例。  
  
```javascript  
Math.hypot(3, 4);  
// Returns 5  
  
Math.hypot(3, "4");  
// Returns 5  
  
Math.hypot(3, "four");  
// Returns NaN   
  
Math.hypot(3, 4, 10);  
// Returns 11.180339887498949  
  
```  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]