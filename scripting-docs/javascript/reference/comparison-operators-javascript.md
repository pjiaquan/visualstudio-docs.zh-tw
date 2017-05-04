---
title: "比較運算子 (JavaScript) | Microsoft Docs"
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
  - "Comparison"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "比較運算子，指令碼"
  - "大於運算子"
  - "比較運算子"
  - "大於或等於運算子"
  - "不同比較運算子"
  - "相同比較運算子"
ms.assetid: 084f90f0-d010-47cf-96dd-13d637fc9b68
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 比較運算子 (JavaScript)
傳回的布林值將說明比較的結果。  
  
## 語法  
  
```  
  
expression1 comparisonoperator expression2  
```  
  
## 參數  
 `expression1`  
 任何運算式。  
  
 `comparisonoperator`  
 任何比較運算子。  
  
 `expression2`  
 任何運算式。  
  
## 備註  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 比較字串時，會使用字串的 Unicode 字元值來進行比較。  
  
 以下敘述可說明根據 `expression1` 和 `expression2` 的型別和值，不同的運算子群組會有不同的行為方式：  
  
 關係運算子：`<`、`>`、`<=`、`>=`  
  
-   嘗試將 `expression1` 及 `expression2` 兩者皆轉換為數字。  
  
-   如果這兩個運算式皆是字串，則會進行字串比較。  
  
-   如果其中一個運算式為 `NaN`，則會傳回 `false`。  
  
-   負數零與正數零相等。  
  
-   負無限大皆小於任何一個數字 \(包含其本身\)。  
  
-   正無限大皆大於任何一個數字 \(包含其本身\)。  
  
 等號比較運算子：`==`、`!=`  
  
-   如果兩個運算式的型別不同，則會嘗試將它們轉換為字串、數字或布林值。  
  
-   `NaN` 不等於任何型別內容 \(包含其本身\)。  
  
-   負數零與正數零相等。  
  
-   `null` 同時等於 `null` 和 `undefined`。  
  
-   如果兩個值是完全相同的字串、數值上相等的數字、相同的物件、同樣的布林值，或者 \(如果型別不同\) 可強制型轉為上述其中一種情況，則兩值視為相等。  
  
-   其他所有的比較都視為不相等。  
  
 識別運算子：`===`、`!==`  
  
 這些運算子的行為方式和等號比較運算子相同，但是有一點例外，就是不會進行型別轉換。  如果兩個運算式的型別不同，這些運算式一定會傳回 `false`。  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)