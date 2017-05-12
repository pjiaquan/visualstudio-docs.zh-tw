---
title: "邏輯 OR 運算子 (||) (JavaScript) | Microsoft Docs"
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
  - "||"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "|| 運算子"
  - "邏輯 OR 運算子"
ms.assetid: 95295331-6269-4311-8391-dc1c68e116ab
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 邏輯 OR 運算子 (||) (JavaScript)
針對兩個運算式執行邏輯分離。  
  
## 語法  
  
```  
  
result = expression1 || expression2  
```  
  
## 參數  
 *result*  
 任何變數。  
  
 *expression1*  
 任何運算式。  
  
 *expression2*  
 任何運算式。  
  
## 備註  
 如果兩個運算式中有一個或是兩者評估為 **True**，則 *result* 會是 **True**。  下表說明如何決定 *result*：  
  
|如果 `expression1` 為|而且 `expression2` 為|則 `result` 會是|  
|------------------------|------------------------|-------------------|  
|True|True|True|  
|True|False|True|  
|False|True|True|  
|False|False|False|  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 會根據下列規則，將非布林值轉換成布林值：  
  
-   所有物件都視為 true。  
  
-   只有在字串為空字串時，才會被視為 false。  
  
-   `null` 和未定義的值都視為 false。  
  
-   只有在數字為 0 時，才會被視為 false。  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)