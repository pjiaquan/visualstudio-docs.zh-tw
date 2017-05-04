---
title: "必須是規則運算式物件 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5016"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 必須是規則運算式物件
您嘗試在 `RegExp` 型別以外的物件上叫用 **RegExp.prototype.toString** 或 **RegExp.prototype.valueOf** 方法。  這種叫用的物件必須是 `RegExp` 型別。  
  
### 若要更正這個錯誤  
  
-   只能在 `RegExp` 型別的物件上叫用 **RegExp.prototype.toString** 或 **RegExp.prototype.valueOf** 方法。  
  
## 請參閱  
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-tw/ab0766e1-7037-45ed-aa23-706f58358c0e)