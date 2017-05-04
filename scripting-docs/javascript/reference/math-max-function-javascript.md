---
title: "Math.max 函式 (JavaScript) | Microsoft Docs"
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
  - "max"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "max 方法"
ms.assetid: f3ea1b8a-5fd0-482a-971b-b7f8e2b9b7eb
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Math.max 函式 (JavaScript)
傳回提供的一組數值運算式中較大者。  
  
## 語法  
  
```  
Math.max([number1[, number2[... [, numberN]]]])   
```  
  
## 備註  
 選擇性 `number1, number2, ..., numberN` 引數是要評估的數值運算式。  
  
 如果沒有提供引數，傳回值會等於 [Number.NEGATIVE\_INFINITY](../../javascript/reference/number-constants-javascript.md)。  如果有任何引數是 `NaN`，則傳回的值也是 `NaN`。  
  
## 範例  
 下列程式碼示範如何取得兩個運算式中較大者。  
  
```javascript  
var x = Math.max(107 - 3,  48 * 90);  
document.write(x);  
  
// Output:  
// 4320  
  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [Math.min 函式](../../javascript/reference/math-min-function-javascript.md)