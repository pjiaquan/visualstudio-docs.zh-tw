---
title: "callee 屬性 (引數) (JavaScript) | Microsoft Docs"
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
  - "callee"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "callee 屬性"
ms.assetid: ad9d4d21-73f0-44f6-8bec-502f3456cd23
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# callee 屬性 (引數) (JavaScript)
傳回正在執行的 `Function` 物件，也就是指定之 `Function` 物件的內文。  
  
## 語法  
  
```  
[function.]arguments.callee  
```  
  
## 備註  
 選擇性的 *function* 引數是目前正在執行的 `Function` 物件。  
  
 `callee` 屬性是 **arguments** 物件的成員，只有在執行相關函式時才可以使用。  
  
 `callee` 屬性的初始值是正在執行的 `Function` 物件。  這樣可以遞迴匿名函式。  
  
## 範例  
  
```javascript  
function factorial(n){  
  if (n <= 0)  
     return 1;  
  else  
     return n * arguments.callee(n - 1)  
}  
document.write(factorial(4));  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用於**：[arguments 物件](../../javascript/reference/arguments-object-javascript.md)&#124; [Function 物件](../../javascript/reference/function-object-javascript.md)  
  
## 請參閱  
 [caller 屬性 \(函式\)](../../javascript/reference/caller-property-function-javascript.md)