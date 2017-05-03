---
title: "不正確的字元集範圍 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5021"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 不正確的字元集範圍 (JavaScript)
您嘗試以無效的字元集範圍建立規則運算式。  字元集必須僅限單一字元範圍，例如 a\-z 或 0\-9。您不得在字元集中包含類似 \\w 的字元類別。  此範圍的第一個字元也必須在此範圍的第二個字元之前。  例如：  
  
```javascript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### 若要更正這個錯誤  
  
-   只能使用單一字元撰寫您的規則運算式字元集，並確定這些都是以正確的順序顯示。  
  
## 請參閱  
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-tw/ab0766e1-7037-45ed-aa23-706f58358c0e)