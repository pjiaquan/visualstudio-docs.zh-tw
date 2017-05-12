---
title: "位元 OR 運算子 (|) (JavaScript) | Microsoft Docs"
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
  - "|"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "| 運算子"
  - "位元運算子, OR 運算子"
  - "OR 運算子"
ms.assetid: ffc8f758-3151-478e-bafb-fc78f1c469a0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 位元 OR 運算子 (|) (JavaScript)
針對兩個運算式執行位元 OR。  
  
## 語法  
  
```  
  
result = expression1 | expression2  
```  
  
## 參數  
 *result*  
 任何變數。  
  
 *expression1*  
 任何運算式。  
  
 *expression2*  
 任何運算式。  
  
## 備註  
 **&#124;** 運算子先檢查兩個運算式值的二進位表示法，然後在兩個運算式上執行位元 OR 運算。  運算結果如下：  
  
```javascript  
0101   (expression1)  
1100   (expression2)  
----  
1101   (result)  
```  
  
 如果任何一個運算式的數字有 1，結果的那個數字就會有 1。  否則，結果會在該數字出現 0。  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [位元 OR 設定運算子 \(&#124;\=\)](../../javascript/reference/bitwise-or-assignment-operator-decrement-equal-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)