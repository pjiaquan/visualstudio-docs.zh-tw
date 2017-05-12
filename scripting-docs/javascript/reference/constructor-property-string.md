---
title: "constructor 屬性 (字串) | Microsoft Docs"
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
ms.assetid: ef0e9c82-4651-4404-87b1-d00cad38c6f9
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor 屬性 (字串)
指定用來建立字串的函式。  
  
## 語法  
  
```  
  
string.constructor  
```  
  
## 備註  
 必要的 `string` 是字串的名稱。  
  
 `constructor` 屬性為每個具有原型之物件的原型成員。  其中包括所有的內建 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 物件，但是 `Global` 和 `Math` 物件除外。  `constructor` 屬性包含建構該特殊物件之執行個體的函式參考。  
  
## 範例  
 以下範例說明如何使用 constructor 屬性。  
  
```javascript  
var x = new String();  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
else  
    document.write("Object is not a String.");  
  
// Output:  
// Object is a String.  
  
```  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]