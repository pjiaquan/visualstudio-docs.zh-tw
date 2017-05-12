---
title: "加法運算子 (+) (JavaScript) | Microsoft Docs"
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
  - "+"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "算術運算子，加法"
  - "字串 [Visual Studio]，串連"
  - "串連運算子，和加法運算子的比較"
  - "加法運算子"
  - "+ 運算子"
ms.assetid: ec1237d3-e78b-4e77-bd7d-c0204cf03acd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 加法運算子 (+) (JavaScript)
將某個數值運算式的值與另一個運算式的值相加，或是串連兩個字串。  
  
## 語法  
  
```  
  
result = expression1 + expression2  
```  
  
## 參數  
 `result`  
 任何變數。  
  
 `expression1`  
 任何運算式。  
  
 `expression2`  
 任何運算式。  
  
## 備註  
 兩個運算式的型別決定 **\+** 運算子的行為。  
  
|If|Then|  
|--------|----------|  
|兩個運算式為數值或布林值|Add|  
|兩個運算式都是字串|Concatenate|  
|一個運算式為數值，另一個是字串|Concatenate|  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [加法設定運算子 \(\+\=\)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)