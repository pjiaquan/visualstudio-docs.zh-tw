---
title: "Math.acos 函式 (JavaScript) | Microsoft Docs"
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
  - "acos"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "acos 方法"
  - "arcosine 方法"
ms.assetid: 828cb3c3-bdf7-4bb7-97ae-3617ce4b2d62
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Math.acos 函式 (JavaScript)
傳回數字的反餘弦 \(或逆餘弦\) 函數值。  
  
## 語法  
  
```  
Math.acos(number)  
```  
  
#### 參數  
 必要的 `number` 引數是數值運算式。  
  
## 傳回值  
 `number` 引數的反餘弦函數，以弧度為單位。  
  
## 範例  
 下列程式碼示範如何使用 `acos` 函式。  
  
```javascript  
var v1 = Math.acos(-1.0);  
var v2 = Math.cos(-1.0);  
  
document.write(v1);  
document.write("<br/>");  
document.write(v2);  
  
// Output:  
// 3.141592653589793  
// 0.5403023058681398  
  
```  
  
## 備註  
 **適用於**：[Math 物件](../../javascript/reference/math-object-javascript.md)  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [Math.asin 函式](../../javascript/reference/math-asin-function-javascript.md)   
 [Math.atan 函式](../../javascript/reference/math-atan-function-javascript.md)   
 [Math.cos 函式](../../javascript/reference/math-cos-function-javascript.md)   
 [Math.sin 函式](../../javascript/reference/math-sin-function-javascript.md)   
 [Math.tan 函式](../../javascript/reference/math-tan-function-javascript.md)   
 [Math 物件](../../javascript/reference/math-object-javascript.md)