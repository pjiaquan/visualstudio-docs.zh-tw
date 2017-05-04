---
title: "Object.getOwnPropertySymbols 函式 (JavaScript) | Microsoft Docs"
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
ms.assetid: 68dd69b9-5a33-44c2-ba5f-21a4ae6c0879
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Object.getOwnPropertySymbols 函式 (JavaScript)
傳回物件的擁有符號屬性。  物件的擁有符號屬性直接定義於該物件上，而且不是繼承自物件的原型。  
  
## 語法  
  
```  
Object.getOwnPropertySymbols(object);  
```  
  
#### 參數  
 `object`  
 必要項。  包含擁有符號的物件。  
  
## 傳回值  
 包含物件之擁有符號的陣列。  
  
## 備註  
 您需要使用 `Object.getOwnPropertySymbols` 才能取得物件的符號屬性。  `Object.getOwnPropertyNames` 將不會傳回符號屬性。  
  
## 範例  
 下列程式碼範例示範如何取得物件的符號屬性。  
  
```javascript  
var obj = {};  
var key = Symbol('description');  
  
obj[key] = 'data';  
  
var symbols = Object.getOwnPropertySymbols(obj);  
  
console.log(s[0].toString());  
  
// Output:  
// undefined  
// Symbol(description)  
```  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]