---
title: "toFixed 方法 (數字) (JavaScript) | Microsoft Docs"
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
  - "toFixed"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toFixed 方法"
ms.assetid: b5f03400-865e-4ab2-818c-f734c0f6d6f0
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# toFixed 方法 (數字) (JavaScript)
代表以定點標記法表示的數字。  
  
## 語法  
  
```  
  
numObj.toFixed([fractionDigits])  
```  
  
## 參數  
 `numObj`  
 必要的 `Number` 物件。  
  
 `fractionDigits`  
 選擇項。  小數點後的位數。  必須在 0 – 20 \(含\) 範圍之內。  
  
## 傳回值  
 以定點標記法傳回數字的字串表式，小數點之後包含 `fractionDigits` 個位數。  
  
 如果 `fractionDigits` 未提供或是**未定義**，則預設值為零。  
  
## 範例  
 下列程式碼示範 `toFixed` 的用法。  
  
```javascript  
var num = new Number(123);  
var fix = num.toFixed();  
document.write(fix);  
document.write("<br/>");  
  
num = new Number(123.456);  
fix = num.toFixed(5);  
document.write(fix);  
  
// Output:  
// 123  
123.45600  
  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用於**：[Number 物件](../../javascript/reference/number-object-javascript.md)  
  
## 請參閱  
 [toExponential 方法 \(數字\)](../../javascript/reference/toexponential-method-number-javascript.md)   
 [toPrecision 方法 \(數字\)](../../javascript/reference/toprecision-method-number-javascript.md)