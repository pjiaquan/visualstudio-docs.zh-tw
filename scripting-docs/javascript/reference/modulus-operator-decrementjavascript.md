---
title: "模數運算子 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "%"
dev_langs: 
  - "JavaScript"
  - "DHTML"
helpviewer_keywords: 
  - "模數運算子，JavaScript"
  - "% 運算子 [JavaScript]"
  - "餘數函式 [JavaScript]"
ms.assetid: 087d654f-623b-498d-95ff-596d26bf674d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 模數運算子 (JavaScript)
以某運算式的值除以另一個運算式的值，並傳回餘數。  
  
## 語法  
  
```  
  
result = number1 % number2  
```  
  
## 引數  
 `result`  
 任何變數。  
  
 `number1`  
 任何數值運算式。  
  
 `number2`  
 任何數值運算式。  
  
## 備註  
 模數或餘數運算子會將 `number1` 除以 `number2`，並且會以 `result` 的方式只傳回餘數。  `result` 的符號與 `number1` 的符號相同。  `result` 的值會介於 0 與 `number2` 的絕對值之間。  
  
 下列程式碼示範如何使用模數運算子。  
  
```  
var modResult = 19 % 6.7;  
document.write(modResult);  
  
// Output: 5.6  
  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)