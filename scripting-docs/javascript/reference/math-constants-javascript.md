---
title: "Math 常數 (JavaScript) | Microsoft Docs"
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
  - "LN2 常數 [JavaScript]"
  - "E 常數 [JavaScript]"
  - "LOG10E 常數 [JavaScript]"
  - "SQRT1_2 常數 [JavaScript]"
  - "LOG2E 常數 [JavaScript]"
  - "Math.SQRT2 常數 [JavaScript]"
  - "PI 常數 [JavaScript]"
  - "Math.LOG2E 常數 [JavaScript]"
  - "常數 [JavaScript]，數學"
  - "Math.E 常數 [JavaScript]"
  - "對數常數 [JavaScript]"
  - "Math.LOG10E 常數 [JavaScript]"
  - "Math.SQRT1_2 常數 [JavaScript]"
  - "SQRT2 常數 [JavaScript]"
  - "平方根常數 [JavaScript]"
  - "Math.PI 常數 [JavaScript]"
  - "數學常數 [JavaScript]"
  - "LN10 常數 [JavaScript]"
  - "Math.LN2 常數 [JavaScript]"
  - "Math.LN10 常數 [JavaScript]"
ms.assetid: 8a674046-cb99-4103-92be-83697fba6344
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Math 常數 (JavaScript)
數學常數會傳回屬於 `Math` 物件屬性的常數值。  
  
## 數學物件常數  
 下表列出屬於 [Math 物件](../../javascript/reference/math-object-javascript.md)屬性的常數值。  
  
|常數|描述|近似值|  
|--------|--------|---------|  
|`Math.E`|數學常數 e。  這是 Euler 數字，也就是自然對數的底數。|2.718|  
|`Math.LN2`|2 的自然對數。|0.693|  
|`Math.LN10`|10 的自然對數。|2.302|  
|`Math.LOG2E`|底數為 2 的 e 對數。|1.443|  
|`Math.LOG10E`|底數為 10 的 e 對數。|0.434|  
|`Math.PI`|Pi。  它代表圓周的周長與直徑的比率。|3.14159|  
|`Math.SQRT1_2`|0.5 的平方根，也就是 1 除以 2 的平方根。|0.707|  
|`Math.SQRT2`|2 的平方根。|1.414|  
  
## 範例  
 下列範例說明如何使用 `Math.PI` 常數。  
  
```javascript  
var radius = 3;  
var area = Math.PI * radius * radius;  
document.write(area);  
  
// Output: 28.274333882308138  
  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[Math 物件](../../javascript/reference/math-object-javascript.md)  
  
## 請參閱  
 [Number 常數](../../javascript/reference/number-constants-javascript.md)   
 [JavaScript 常數](../../javascript/reference/javascript-constants.md)