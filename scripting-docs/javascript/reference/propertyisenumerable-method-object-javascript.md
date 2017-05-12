---
title: "propertyIsEnumerable 方法 (Object) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "propertyIsEnumerable"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "propertyIsEnumerable 屬性"
ms.assetid: d90c7c2e-ea23-4710-a957-9aefbbd1f68b
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# propertyIsEnumerable 方法 (Object) (JavaScript)
判斷指定的屬性是否可列舉。  
  
## 語法  
  
```  
  
object. propertyIsEnumerable(proName)  
```  
  
## 參數  
 `object`  
 必要項。  物件的執行個體。  
  
 `proName`  
 必要項。  屬性名稱的字串值。  
  
## 備註  
 如果 `proName` 存在於 `object` 中而且可以使用 `For` 迴圈列舉，`propertyIsEnumerable` 方法會傳回 `true`。  如果 `object` 沒有指定名稱的屬性，或是指定的屬性無法列舉，`propertyIsEnumerable` 屬性會傳回 `false`。  一般而言，預先定義的屬性無法列舉，但是使用者定義的屬性一律可列舉。  
  
 `propertyIsEnumerable` 方法不會考慮原型鏈結中的物件。  
  
## 範例  
  
```javascript  
var a = new Array("apple", "banana", "cactus");  
document.write(a.propertyIsEnumerable(1));  
  
// Output: true  
  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 請參閱  
 [prototype 屬性 \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)