---
title: "Math.log 函式 (JavaScript) | Microsoft Docs"
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
  - "log"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "log 方法"
  - "Math 物件"
ms.assetid: 5d617fb5-4b27-404e-842f-eea5549a7c1a
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Math.log 函式 (JavaScript)
傳回數字的自然對數 \(底數為 `e`\)。  
  
## 語法  
  
```  
Math.log(number)   
```  
  
#### 參數  
 number  
 數字。  
  
## 傳回值  
 如果 `number` 為正數，這個函式就傳回數字的自然對數。  如果 `number` 為負數，這個函式會傳回 `NaN`。  如果 `number` 為 0，這個函式會傳回 `-Infinity`。  
  
## 範例  
 下列程式碼示範如何使用這個函式。  
  
```javascript  
var numArr = [ 45.3, 69.0, 557.04, 0.222 ];  
  
for (i in numArr) {  
    document.write(Math.log(numArr[i]));  
    document.write("<br/>");  
}  
  
// Output:   
// 3.8133070324889884  
// 4.23410650459726  
// 6.322637050634291  
// -1.5050778971098575  
  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[Math 物件](../../javascript/reference/math-object-javascript.md)  
  
## 請參閱  
 [Math.sqrt 函式](../../javascript/reference/math-sqrt-function-javascript.md)