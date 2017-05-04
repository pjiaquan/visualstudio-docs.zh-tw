---
title: "加法指派運算子 (+=) (JavaScript) | Microsoft Docs"
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
  - "+="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "加法指派運算子 (+=)"
  - "+= 運算子"
  - "指派運算子，JavaScript"
ms.assetid: 8517d05c-38b0-4107-bea4-253eb420f438
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# 加法指派運算子 (+=) (JavaScript)
將運算式的值加入至變數值，然後將結果指派給變數。  
  
## 語法  
  
```  
  
result += expression   
```  
  
## 參數  
 `result`  
 任何變數。  
  
 `expression`  
 任何運算式。  
  
## 備註  
 使用這個運算子與以下的指定方式完全相同：`result = result + expression`。  
  
 兩個運算式的型別決定 `+=` 運算子的行為。  
  
|If|Then|  
|--------|----------|  
|兩個運算式為數值或布林值|Add|  
|兩個運算式都是字串|Concatenate|  
|一個運算式為數值，另一個是字串|Concatenate|  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [加法運算子 \(\+\)](../../javascript/reference/addition-operator-decrement-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)