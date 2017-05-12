---
title: "必須要有陣列或引數物件 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5028"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 22b83e2f-8916-46db-8d8c-50c8481b7c90
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 必須要有陣列或引數物件
您並未提供陣列做為引數。  這個錯誤僅適用於 **Function.prototype.apply** 方法。  如果有為這個函式指定第二個引數，該引數必須為 `Array` 物件或 **Arguments** 物件。  
  
### 若要更正這個錯誤  
  
-   請指定 `Array` 或 **Arguments** 物件做為第二個引數。  
  
## 請參閱  
 [使用陣列](../../javascript/advanced/using-arrays-javascript.md)   
 [apply 方法 \(函式\)](../../javascript/reference/apply-method-function-javascript.md)   
 [函式](../../javascript/functions-javascript.md)