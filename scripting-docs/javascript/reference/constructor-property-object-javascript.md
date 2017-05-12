---
title: "constructor 屬性 (Object) (JavaScript) | Microsoft Docs"
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
  - "constructor"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "constructor 屬性"
ms.assetid: 6f5d0e9d-e85f-4fde-b558-744510483d69
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# constructor 屬性 (Object) (JavaScript)
指定用來建立物件的函式。  
  
## 語法  
  
```  
  
object.constructor  
```  
  
## 備註  
 必要的 `object` 是物件或函式的名稱。  
  
 `constructor` 屬性為每個具有原型之物件的原型成員。  其中包括所有的內建 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 物件，但是 `Global` 和 `Math` 物件除外。  `constructor` 屬性包含建構該特殊物件之執行個體的函式參考。  
  
## 範例  
 以下範例說明如何使用 constructor 屬性。  
  
```javascript  
// A constructor function.  
function MyObj() {  
    this.number = 1;  
}  
  
var x = new String("Hi");  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
document.write ("<br />");  
  
var y = new MyObj;  
if (y.constructor == MyObj)  
    document.write("Object constructor is MyObj.");  
  
// Output:  
// Object is a String.  
// Object constructor is MyObj.  
  
```  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## 請參閱  
 [prototype 屬性 \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)