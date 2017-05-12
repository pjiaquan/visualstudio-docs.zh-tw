---
title: "必須是 Boolean | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5010"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 必須是 Boolean
您嘗試針對型別不是 `Boolean` 的物件叫用 **Boolean.prototype.toString** 或 **Boolean.prototype.valueOf** 方法。  這種叫用的目標物件必須是 `Boolean` 型別。  例如：  
  
```javascript  
var o = new Object;  
o.f = Boolean.prototype.toString;  
o.f();  
```  
  
### 若要更正這個錯誤  
  
-   您只能針對型別是 **Boolean** 的物件叫用 **Boolean.prototype.toString** 或 **Boolean.prototype.valueOf** 方法。  
  
## 請參閱  
 [Boolean 物件](../../javascript/reference/boolean-object-javascript.md)   
 [資料類型](../../javascript/data-types-javascript.md)   
 [控制程式流程](../../javascript/controlling-program-flow-javascript.md)   
 [複製、傳遞和比較資料](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)