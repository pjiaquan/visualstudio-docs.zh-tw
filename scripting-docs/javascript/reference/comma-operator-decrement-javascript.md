---
title: "逗號運算子 (,) (JavaScript) | Microsoft Docs"
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
  - "%2C"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "逗號運算子"
ms.assetid: 699fa0bf-cd0a-45ee-a291-2fbed4ecd470
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 逗號運算子 (,) (JavaScript)
能夠連續執行兩個運算式。  
  
## 語法  
  
```  
  
expression1, expression2  
```  
  
## 參數  
 `expression1`  
 任何運算式。  
  
 `expression2`  
 任何運算式。  
  
## 備註  
 `,` 運算子會造成運算式從左至右執行。  `,` 運算子常用於 `for` 迴圈的遞增運算式中。  例如：  
  
```javascript  
j=25;  
for (i = 0; i < 10; i++, j++)  
{  
   k = i + j;  
}  
```  
  
 `for` 陳述式只允許在每次通過迴圈的結尾時執行一個運算式。  `,` 運算子允許將多個運算式視為單一運算式，因此這兩個變數都可以遞增。  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [for 陳述式](../../javascript/reference/for-statement-javascript.md)   
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)