---
title: "Number 常數 (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "常數 [JavaScript], 數字"
  - "MAX_VALUE 常數 [JavaScript]"
  - "MIN_VALUE 常數 [JavaScript]"
  - "NaN 常數 [JavaScript]"
  - "NEGATIVE_INFINITY 常數 [JavaScript]"
  - "數字常數 [JavaScript]"
  - "Number.MAX_VALUE 常數 [JavaScript]"
  - "Number.MIN_VALUE 常數 [JavaScript]"
  - "Number.NaN 常數 [JavaScript]"
  - "Number.NEGATIVE_INFINITY 常數 [JavaScript]"
  - "Number.POSITIVE_INFINITY 常數 [JavaScript]"
  - "POSITIVE_INFINITY 常數 [JavaScript]"
ms.assetid: e0701b41-99ae-4916-9ec0-f79bb15386fb
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Number 常數 (JavaScript)
下列數字常數是 `Number` 物件的屬性。  
  
## Number 物件常數  
 您不需要建立 `Number` 物件來存取這些常數。  
  
|常數|傳回的值|  
|--------|----------|  
|`Number.EPSILON`|可在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中表示的最小數字。  約等於 2.2204460492503130808472633361816E\-16。|  
|`Number.MAX_SAFE_INTEGER`|可在 JavaScript 中安全表示的最大數字。  等於 9007199254740991。|  
|`Number.MAX_VALUE`|可在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中表示的最大數字。  約等於 1.79E\+308。|  
|`Number.MIN_SAFE_INTEGER`|可在 JavaScript 中安全表示的最小數字。  等於 −9007199254740991。|  
|`Number.MIN_VALUE`|可在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中表示，最接近零的數字。  約等於 5.00E\-324。|  
|`Number.NaN`|不是數字的值。<br /><br /> 在相等比較中，`NaN` 不等於任何值，包括它自己。  若要測試一個值是否等於 `NaN`，請使用 [isNaN 函式](../../javascript/reference/isnan-function-javascript.md)。|  
|`Number.NEGATIVE_INFINITY`|小於可在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中表示之最大負數的值。<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 會將 `NEGATIVE_INFINITY` 值顯示為 `-infinity`。|  
|`Number.POSITIVE_INFINITY`|大於可在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中表示之最大數字的值。<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 會將 `POSITIVE_INFINITY` 值顯示為 `infinity`。|  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 對於 `Number.EPSILON``Number.MAX_SAFE_INTEGER` 和 `Number.MIN_SAFE_INTEGER`：  
  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **適用於**：[Number 物件](../../javascript/reference/number-object-javascript.md)  
  
## 請參閱  
 [Math 常數](../../javascript/reference/math-constants-javascript.md)   
 [JavaScript 常數](../../javascript/reference/javascript-constants.md)   
 [Infinity 常數](../../javascript/reference/infinity-constant-javascript.md)   
 [NaN 常數](../../javascript/reference/nan-constant-javascript.md)   
 [isNaN 函式](../../javascript/reference/isnan-function-javascript.md)