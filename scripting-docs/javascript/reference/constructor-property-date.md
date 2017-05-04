---
title: "constructor 屬性 (日期) | Microsoft Docs"
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
ms.assetid: 5db153a1-788b-4a61-bfc8-2d2ec38f36ea
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor 屬性 (日期)
指定用來建立日期的函式。  
  
## 語法  
  
```  
  
date.constructor  
```  
  
## 備註  
 必要的 `date` 是日期物件的名稱。  
  
 `constructor` 屬性為每個具有原型之物件的原型成員。  `constructor` 屬性包含建構該特殊物件之執行個體的函式參考。  
  
## 範例  
 以下範例說明如何使用 constructor 屬性。  
  
```javascript  
var x = new Date("Hi");  
  
if (x.constructor == Date)  
    document.write("Object is a date.");  
  
// Output:  
// Object is a date.  
  
```  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]