---
title: "void 運算子 (JavaScript) | Microsoft Docs"
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
  - "void_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "void 運算子"
ms.assetid: c054bc7e-8341-42e6-b227-4d7b196f60d8
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# void 運算子 (JavaScript)
避免運算式傳回值。  
  
## 語法  
  
```  
void expression   
```  
  
## 備註  
 `expression` 引數是任何有效的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 運算式。  
  
 `void` 運算子會計算其運算式的結果，然後傳回 `undefined`。  這最適用的情況是在應該評估運算式但不要讓指令碼的其餘部分看見該結果的時候。  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## 請參閱  
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)