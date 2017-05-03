---
title: "toPrecision 方法 (數字) (JavaScript) | Microsoft Docs"
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
  - "toPrecision"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toPrecision 方法"
ms.assetid: ac13c82f-1038-447a-823f-f755bba535ca
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toPrecision 方法 (數字) (JavaScript)
代表以指數或定點標記法表示的數字 \(有指定數字的位數\)。  
  
## 語法  
  
```  
  
numObj.toPrecision([precision])  
```  
  
## 參數  
 `numObj`  
 必要項。  `Number` 物件。  
  
 `precision`  
 選擇項。  有效位數。  必須在 1 – 21 \(含\) 範圍之內。  
  
## 傳回值  
 對於採用指數標記法的數字，傳回的數字是小數點後 `precision` \- 1 位數。  對於採用定點標記法的數字，傳回的有效位數是 `precision`。  
  
 如果 `precision` 未指定或是 **undefined**，則應改呼叫 **toString** 方法。  
  
## 範例  
 在下列範例程式碼中，會示範 `toPrecision` 的用法。  
  
```javascript  
var num = new Number(123);  
var prec = num.toPrecision();  
document.write(prec);  
document.write("<br/>");  
  
num = new Number(123.456);  
prec = num.toPrecision(5);  
document.write(prec);  
  
// Output:  
// 123  
// 123.46  
  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用於**：[Number 物件](../../javascript/reference/number-object-javascript.md)  
  
## 請參閱  
 [toFixed 方法 \(數字\)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toExponential 方法 \(數字\)](../../javascript/reference/toexponential-method-number-javascript.md)