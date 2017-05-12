---
title: "isNaN 函式 (JavaScript) | Microsoft Docs"
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
  - "isNaN"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "isNaN 方法"
ms.assetid: 5af4eb29-72f6-484f-93bd-04ae1261f849
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# isNaN 函式 (JavaScript)
傳回的布林值將說明數值是否為保留值 `NaN` \(非數值\)。  
  
## 語法  
  
```  
isNaN(numValue)   
```  
  
## 傳回值  
 如果轉換為 `Number` 類型的值為 `NaN` 則為 `true`，否則為 `false`。  
  
## 備註  
 必要的 `numValue` 是要針對 `NaN` 進行測試的值。  
  
 您通常會使用此方法來測試 `parseInt` 和 `parseFloat` 方法的傳回值。  
  
 另外，包含 `NaN` 或其他值的變數也可以與其本身比較。  如果比較結果不相等，則它會是 `NaN`。  原因是 `NaN` 是唯一與其本身不相等的值。  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[Global 物件](../../javascript/reference/global-object-javascript.md)  
  
## 範例  
  
```javascript  
// Returns false.  
isNaN(100);  
  
// Returns false.  
isNaN("100");  
  
// Returns true.  
isNaN("ABC");  
  
// Returns true.  
isNaN("10C");  
  
// Returns true.  
isNaN("abc123");  
  
// Returns true.  
isNaN(Math.sqrt(-1));           
```  
  
## 請參閱  
 [isFinite 函式](../../javascript/reference/isfinite-function-javascript.md)   
 [NaN 常數](../../javascript/reference/nan-constant-javascript.md)   
 [parseFloat 函式](../../javascript/reference/parsefloat-function-javascript.md)   
 [parseInt 函式](../../javascript/reference/parseint-function-javascript.md)