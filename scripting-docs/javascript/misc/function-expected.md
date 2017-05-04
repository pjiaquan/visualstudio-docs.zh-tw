---
title: "必須是 Function | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5002"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 必須是 Function
您嘗試針對非 `Function` 的物件叫用其中一個**函式原型**方法，或者您在函式呼叫內容中使用了物件。  例如，下列程式碼會產生這個錯誤，因為 **example** 不是函式。  
  
```javascript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### 若要更正這個錯誤  
  
-   只能在 `Function` 物件上呼叫**函式原型**方法。  
  
-   務必只能使用函式呼叫運算子 `()` 呼叫函式。  
  
## 請參閱  
 [Function 物件](../../javascript/reference/function-object-javascript.md)   
 [prototype 屬性 \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)