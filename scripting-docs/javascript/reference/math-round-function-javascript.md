---
title: "Math.round 函式 (JavaScript) | Microsoft Docs"
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
  - "round"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Math 物件"
  - "Round 方法"
ms.assetid: 51008df3-5d0c-4951-84cb-4f41000db0be
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Math.round 函式 (JavaScript)
傳回提供的數值運算式 \(四捨五入到最近的整數\)。  
  
## 語法  
  
```  
  
Math.round(  
number  
)   
```  
  
## 備註  
 必要的 `number` 引數是要四捨五入到最近整數的值。  
  
 對於正數而言，如果 `number` 的小數部分是 0.5 或大於 0.5，則傳回值為大於 `number` 的最小整數。  如果小數部分小於 0.5，則傳回值是小於或等於 `number` 的最大整數。  
  
 對於負數而言，如果小數部分剛好是 \-0.5，則傳回值是大於該數字的最小整數。  
  
 例如，`Math.round(8.5)` 會傳回 9，但 `Math.round(-8.5)` 會傳回 \-8。  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[Math 物件](../../javascript/reference/math-object-javascript.md)  
  
## 請參閱  
 [Math.random 函式](../../javascript/reference/math-random-function-javascript.md)