---
title: "isPrototypeOf 方法 (Object) (JavaScript) | Microsoft Docs"
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
  - "isPrototypeOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "isPrototypeOf 方法"
ms.assetid: 9c821319-c208-480f-915e-565ef6e017b6
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# isPrototypeOf 方法 (Object) (JavaScript)
判斷某個物件是否存在於另一個物件的原型鏈結中。  
  
## 語法  
  
```  
  
prototype.isPrototypeOf(object)  
```  
  
## 參數  
 `prototype`  
 必要項。  物件原型。  
  
 `object`  
 必要項。  將檢查其原型鏈結的另一個物件。  
  
## 備註  
 如果 `object` 的原型鏈結中有 `prototype`，則 `isPrototypeOf` 方法會傳回 `true`。  原型鏈結可用來在同一種物件類型的執行個體之間共用功能。  當 `object` 不是物件或是 `prototype` 沒有出現在 `object` 的原型鏈結中時，`isPrototypeOf` 方法會傳回 `false`。  
  
## 範例  
 在下列程式碼中，說明了如何使用 `isPrototypeOf` 方法。  
  
```javascript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
document.write(Rectangle.prototype.isPrototypeOf(rec));  
  
// Output: true  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 請參閱  
 [prototype 屬性 \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)