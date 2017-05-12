---
title: "邏輯 NOT 運算子 (!)(JavaScript) | Microsoft Docs"
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
  - "!"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "! 運算子"
  - "! 運算子, 關於 ! 運算子"
  - "邏輯 NOT 運算子"
ms.assetid: 68c3dc71-ae95-4293-9155-67405846d71d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 邏輯 NOT 運算子 (!)(JavaScript)
在運算式上執行邏輯負運算。  
  
## 語法  
  
```  
  
result = !expression  
```  
  
## 參數  
 *result*  
 任何變數。  
  
 *expression*  
 任何運算式。  
  
## 備註  
 下表說明如何決定 *result*。  
  
|如果 `expression` 為|則 `result` 為|  
|-----------------------|------------------|  
|True|False|  
|False|True|  
  
 所有的一元運算子 \(如 **\!** 運算子\) 都會依照下列方式評估運算式：  
  
-   如果套用到未定義或 `null` 運算式，則會發生執行階段錯誤。  
  
-   物件會轉換成字串。  
  
-   如果可能的話，字串會轉換成數字。  如果不行，就會發生執行階段錯誤。  
  
-   布林值會被當做數字處理 \(如果為 false 則是 0，為 true 則是 1\)。  
  
 接著，這個運算子會套用到產生的數字。  
  
 就 **\!** 運算子來說，如果 *expression* 是非零值，則 *result* 為零。  如果 *expression* 是零，則 *result* 為 1。  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [位元 NOT 運算子 \(~\)](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)