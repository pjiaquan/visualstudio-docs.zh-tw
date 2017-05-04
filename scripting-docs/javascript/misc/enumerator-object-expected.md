---
title: "必須是 Enumerator 物件 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5015"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 必須是 Enumerator 物件
您嘗試針對 `Enumerator` 型別以外的物件叫用 **Enumerator.prototype.atEnd、Enumerator.prototype.item、Enumerator.prototype.moveFirst、** 或 **Enumerator.prototype.moveNext** 方法。  這種叫用的物件必須是 `Enumerator` 型別。  以下是違反此規則的程式碼範例：  
  
```javascript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### 若要更正這個錯誤  
  
-   只能針對 `Enumerator` 型別的物件叫用 **Enumerator.prototype.atEnd**、**Enumerator.prototype.item**、**Enumerator.prototype.moveFirst** 或 **Enumerator.prototype.moveNext** 方法。  若要了解您的物件是否為 `Enumerator` 物件，請使用：  
  
    ```  
    if(x instanceof Enumerator)  
    ```  
  
## 請參閱  
 [Enumerator 物件](../../javascript/reference/enumerator-object-javascript.md)