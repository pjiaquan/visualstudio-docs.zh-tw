---
title: "toExponential 方法 (數字) (JavaScript) | Microsoft Docs"
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
  - "toExponential"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toExponential 方法"
ms.assetid: 7c4a6d84-3c1f-4cc4-a67d-7753e5d4ed66
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toExponential 方法 (數字) (JavaScript)
表示採用指數標記法的數字。  
  
## 語法  
  
```  
  
numObj. toExponential([fractionDigits])  
```  
  
## 參數  
 `numObj`  
 必要項。  **Number** 物件。  
  
 `fractionDigits`  
 選擇項。  小數點後的位數。  必須在 0 – 20 \(含\) 範圍之內。  
  
## 傳回值  
 會以字串方式傳回採用指數標記法的數字。  字串包含小數點的前一位數，後面可跟著 `fractionDigits` 位數。  
  
 如果未提供 `fractionDigits`，`toExponential` 方法會視需要傳回位數，使得數字不會重複。  
  
## 範例  
  
```javascript  
var num = new Number(123);  
var exp = num.toExponential();  
document.write(exp);  
document.write("<br/>");  
  
num = new Number(123.456);  
exp = num.toExponential(5);  
document.write(exp);  
  
// Output:   
// 1.23e+2  
// 1.23456e+2  
  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用於**：[Number 物件](../../javascript/reference/number-object-javascript.md)  
  
## 請參閱  
 [toFixed 方法 \(數字\)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toPrecision 方法 \(數字\)](../../javascript/reference/toprecision-method-number-javascript.md)