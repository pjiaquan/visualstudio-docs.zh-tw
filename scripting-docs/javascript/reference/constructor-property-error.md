---
title: "constructor 屬性 (錯誤) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 18aea278-2bd5-457b-83a5-d8d8f1226e0c
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor 屬性 (錯誤)
指定用來建立錯誤的函式。  
  
## 語法  
  
```  
  
error.constructor  
```  
  
## 備註  
 必要的 `error` 是錯誤物件的名稱。  
  
 `constructor` 屬性為每個具有原型之物件的原型成員。  `constructor` 屬性包含建構該特殊物件之執行個體的函式參考。  
  
## 範例  
 以下範例說明如何使用 constructor 屬性。  
  
```javascript  
var x = new Error("This is an error");  
  
if (x.constructor == Error)  
    document.write("Object is an error.");  
  
// Output:  
// Object is an error.  
  
```  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]