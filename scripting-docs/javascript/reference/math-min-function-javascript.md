---
title: "Math.min 函式 (JavaScript) | Microsoft Docs"
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
  - "min"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "min 方法"
ms.assetid: a1d7dd85-27ef-45cd-aa2a-f8e80f0b2898
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Math.min 函式 (JavaScript)
傳回一組較小的數值運算式。  
  
## 語法  
  
```  
Math.min([number1[, number2[... [,numberN]]]])  
```  
  
## 備註  
 選擇性 `number1, number2, ..., numberN` 引數是要評估的數值運算式。  
  
 如果沒有提供引數，傳回的值會等於 [Number.POSITIVE\_INFINITY](../../javascript/reference/number-constants-javascript.md)。  如果有任何引數是 `NaN`，則傳回的值也是 `NaN`。  
  
## 範例  
 下列程式碼示範如何取得兩個運算式中較小的那一個。  
  
```javascript  
var x = Math.min(107 - 3, 48 * 90);  
document.write(x);  
  
// Output:  
// 104  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [Math.max 函式](../../javascript/reference/math-max-function-javascript.md)