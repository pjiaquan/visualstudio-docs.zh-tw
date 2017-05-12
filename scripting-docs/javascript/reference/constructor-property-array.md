---
title: "constructor 屬性 (陣列) | Microsoft Docs"
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
ms.assetid: b78d517b-cb56-4866-b30f-ef8121a27843
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor 屬性 (陣列)
指定用來建立陣列的函式。  
  
## 語法  
  
```  
  
array.constructor  
```  
  
## 備註  
 必要的 `array` 是陣列的名稱。  
  
 `constructor` 屬性為每個具有原型之物件的原型成員。  其中包括所有的內建 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 物件，但是 `Global` 和 `Math` 物件除外。  `constructor` 屬性包含建構該特殊物件之執行個體的函式參考。  
  
## 範例  
 以下範例說明如何使用 constructor 屬性。  
  
```javascript  
var x = new Array();  
  
if (x.constructor == Array)  
    document.write("Object is an Array.");  
else  
    document.write("Object is not an Array.");  
  
// Output:  
// Object is an Array.  
  
```  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]