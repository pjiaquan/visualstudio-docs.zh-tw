---
title: "必須是 Date 物件 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5006"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 必須是 Date 物件
您嘗試在 `Date` 型別以外的物件上叫用 **Date.prototype.toString** 或 **Date.prototype.valueOf** 方法。  這種叫用的物件必須是 `Date` 型別。  例如：  
  
```javascript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### 若要更正這個錯誤  
  
-   只能在 `Date` 型別的物件上叫用 **Date.prototype.toString** 或 **Date.prototype.valueOf** 方法。  
  
## 請參閱  
 [Date 物件](../../javascript/reference/date-object-javascript.md)   
 [getDate 方法 \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [內建物件](../../javascript/intrinsic-objects-javascript.md)