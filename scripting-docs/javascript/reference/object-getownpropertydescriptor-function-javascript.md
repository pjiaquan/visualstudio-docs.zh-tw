---
title: "Object.getOwnPropertyDescriptor 函式 (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "getOwnPropertyDescriptor 方法 [JavaScript]"
ms.assetid: 8f0e1c90-c4f9-44c4-bf76-726bacecbc14
caps.latest.revision: 45
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 45
---
# Object.getOwnPropertyDescriptor 函式 (JavaScript)
取得指定物件特有的屬性描述元。  特有的屬性描述元是直接對物件定義而不是從物件原型繼承而來的描述元。  
  
## 語法  
  
```  
Object.getOwnPropertyDescriptor(object, propertyname)  
```  
  
## 參數  
 `object`  
 必要項。  包含屬性的物件。  
  
 `propertyname`  
 必要項。  屬性的名稱。  
  
## 傳回值  
 屬性的描述元。  
  
## 備註  
 您可以使用 `Object.getOwnPropertyDescriptor` 函式取得描述該屬性 \(property\) 之屬性 \(attribute\) 的描述元物件。  
  
 [Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md) 可用於新增或修改屬性。  
  
## 資料屬性範例  
 下列範例會取得資料的屬性描述元，並使用該描述元將屬性設為唯讀。  
  
```javascript  
// Create a user-defined object.  
var obj = {};  
  
// Add a data property.  
obj.newDataProperty = "abc";  
  
// Get the property descriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// Change a property attribute.  
descriptor.writable = false;  
Object.defineProperty(obj, "newDataProperty", descriptor);  
  
```  
  
 如果要列出該屬性的屬性，可以將下列程式碼加入此範例。  
  
```javascript  
// Get the descriptor from the object.  
var desc2 = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// List the descriptor attributes.  
for (var prop in desc2) {  
    document.write(prop + ': ' + desc2[prop]);  
    document.write("<br />");  
}  
  
// Output:  
// value: abc  
// writable: false  
// enumerable: true  
// configurable: true  
```  
  
## 需求  
 [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] 支援所有的功能。  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)] 支援 DOM 物件，但不支援使用者定義的物件。  `enumerable` 和 `configurable` 屬性可以指定，但不會加以使用。  
  
## 請參閱  
 [文件物件模型原型，第二部分：支援存取子 \(getter\/setter\)](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md)