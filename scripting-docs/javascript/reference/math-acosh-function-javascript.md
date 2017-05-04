---
title: "Math.acosh 函式 (JavaScript) | Microsoft Docs"
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
ms.assetid: 881dd2a0-36a5-403b-a3dc-523d8e1e1317
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Math.acosh 函式 (JavaScript)
傳回數字的雙曲反餘弦 \(或反雙曲餘弦\)。  
  
## 語法  
  
```  
Math.acosh(number)  
```  
  
#### 參數  
 所需要的 `number` 引數是數字運算式。  
  
## 傳回值  
 `number` 引數的反雙曲餘弦 \(弧度\)。  
  
## 範例  
 下列程式碼示範如何使用 `acosh` 函式。  
  
```javascript  
var v1 = Math.acosh(3);  
vary v2 = Math.acosh(-1);  
  
document.write(v1);  
document.write("</br>");  
document.write(v2);  
  
// Output:  
// 1.762747174039086  
// NaN  
  
```  
  
## 備註  
 **適用對象**：[Math 物件](../../javascript/reference/math-object-javascript.md)  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## 請參閱  
 [Math.acos 函式](../../javascript/reference/math-acos-function-javascript.md)   
 [Math.asin 函式](../../javascript/reference/math-asin-function-javascript.md)   
 [Math.atan 函式](../../javascript/reference/math-atan-function-javascript.md)   
 [Math.cos 函式](../../javascript/reference/math-cos-function-javascript.md)   
 [Math.sin 函式](../../javascript/reference/math-sin-function-javascript.md)   
 [Math.tan 函式](../../javascript/reference/math-tan-function-javascript.md)   
 [Math 物件](../../javascript/reference/math-object-javascript.md)