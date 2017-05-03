---
title: "遞增 (++) 和遞減 (--) 運算子 (JavaScript) | Microsoft Docs"
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
  - "--"
  - "++"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "遞增運算子，語法"
  - "++ 運算子"
  - "++ 運算子，關於 ++ 運算子"
  - "遞減運算子，語法"
  - "-- 運算子"
ms.assetid: 49eaf4cf-8818-478d-a429-cdd2ece20811
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 遞增 (++) 和遞減 (--) 運算子 (JavaScript)
遞增運算子每次將變數的值加一，而遞減運算子則每次將變數的值減一。  
  
## 語法  
  
```  
  
      result = ++variable  
result = --variable  
result = variable++  
result = variable--  
```  
  
## 參數  
 `result`  
 任何變數。  
  
 `variable`  
 任何變數。  
  
## 備註  
 如果運算子在變數之前出現，則會在評估運算式之前修改值。  如果運算子在變數之後出現，則會在評估運算式之後修改值。  換句話說，若指定 `j = ++k;`，則 `j` 的值是 `k` 的原始值加一；若指定 `j = k++;`，則 `j` 的值是 `k` 的原始值，k 會在其值指派給 `j` 之後遞增。  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)