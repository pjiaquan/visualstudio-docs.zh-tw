---
title: "位元 OR 指派運算子 (|=) (JavaScript) | Microsoft Docs"
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
  - "|="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "|= 運算子"
  - "指派運算子, 位元 [JavaScript]"
  - "位元運算子, OR 運算子"
  - "OR 運算子"
ms.assetid: 9b424ff6-4442-4621-b3b6-83e7fd1e5cd5
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 位元 OR 指派運算子 (|=) (JavaScript)
針對變數值和運算式的值執行位元 OR，然後將結果指派給變數。  
  
## 語法  
  
```  
  
result |= expression  
```  
  
## 參數  
 *result*  
 任何變數。  
  
 *expression*  
 任何運算式。  
  
## 備註  
 使用這個運算子與以下的指定方式完全相同：  
  
```javascript  
result = result | expression  
```  
  
 **&#124;\=** 運算子會先檢查以二進位表示的 *result* 及 *expression* 值，然後針對這兩個值執行位元 OR 運算。  這項作業的結果如下：  
  
```javascript  
0101    (result)  
1100    (expression)  
----  
1101    (output)  
```  
  
 如果其中一個運算式的數字為 1，結果會在該數字出現 1。  否則，結果值中的該位數為 0。  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [位元 OR 運算子 \(&#124;\)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)