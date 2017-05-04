---
title: "條件 (三元) 運算子 (?:) (JavaScript) | Microsoft Docs"
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
  - "?:"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "條件 (三元) 運算子"
  - "條件運算子"
  - "三元"
ms.assetid: 7399ac32-9324-4a9a-ae76-be9c0f9df81c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 條件 (三元) 運算子 (?:) (JavaScript)
根據條件傳回兩個運算式的其中一個。  
  
## 語法  
  
```  
  
test ? expression1 : expression2  
```  
  
## 參數  
 `test`  
 任何布林運算式。  
  
 `expression1`  
 如果 `test` 為 `true`，則傳回運算式。  可以是逗號運算子。  
  
 `expression2`  
 如果 `test` 為 `false`，則傳回運算式。  多個運算式可藉由逗號運算式連結。  
  
## 備註  
 `?:` 運算子可當做 `if...else` 陳述式的簡短表示方式。  在一些大型運算式中，若使用 `if...else` 陳述式會顯得很冗長，通常會使用這類簡短表示方式。  例如：  
  
```javascript  
var now = new Date();  
var greeting = "Good" + ((now.getHours() > 17) ? " evening." : " day.");  
```  
  
 上述範例會在下午 6 點後建立包含 "Good evening." 的字串。  使用 `if...else` 陳述式的同等程式碼看起來會像這樣：  
  
```javascript  
var now = new Date();  
var greeting = "Good";  
if (now.getHours() > 17)  
   greeting += " evening.";  
else  
   greeting += " day.";  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [if...else 陳述式](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)   
 [指令碼愛用者組態 Widget 範例應用程式](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)