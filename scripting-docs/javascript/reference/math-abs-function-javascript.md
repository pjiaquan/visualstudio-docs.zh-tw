---
title: "Math.abs 函式 (JavaScript) | Microsoft Docs"
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
  - "abs"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "絕對值，計算"
  - "絕對值"
  - "數值運算式"
  - "abs 方法"
ms.assetid: 9af4b5b8-de77-47bb-bb59-abdde371e4c3
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Math.abs 函式 (JavaScript)
傳回數字的絕對值 \(不考慮是正數還是負數的值\)。  例如，\-5 的絕對值和 5 的絕對值相同。  
  
## 語法  
  
```  
Math.abs(number)  
```  
  
#### 參數  
 必要的 `number` 引數是需要絕對值的數值運算式。  
  
## 傳回值  
 `number` 引數的絕對值。  
  
## 範例  
 以下範例說明 `abs` 函式的用法：  
  
```javascript  
var s;  
var v1 = Math.abs(6);  
var v2 = Math.abs(-6);  
if (v1 == v2) {  
    document.write("Absolute values are the same.");  
}  
else {  
document.write("Absolute values are different.");  
}  
  
// Output: Absolute values are the same.  
  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[Math 物件](../../javascript/reference/math-object-javascript.md)  
  
## 請參閱  
 [Math 物件](../../javascript/reference/math-object-javascript.md)