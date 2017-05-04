---
title: "Object.getPrototypeOf 函式 (JavaScript) | Microsoft Docs"
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
  - "getPrototypeOf 函式 [JavaScript]"
  - "Object.getPrototypeOf 函式 [JavaScript]"
ms.assetid: 1c59cd7a-a7e2-4c5c-83ec-e6bd2b104d9f
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Object.getPrototypeOf 函式 (JavaScript)
傳回物件的原型。  
  
## 語法  
  
```javascript  
Object.getPrototypeOf(object)  
```  
  
#### 參數  
 `object`  
 必要項。  參考原型的物件。  
  
## 傳回值  
 `object` 引數的原型。  這個原型也是物件。  
  
## 例外狀況  
 如果 `object` 不是物件，就會擲回 `TypeError` 例外狀況。  
  
## 範例  
 以下範例說明 `Object.getPrototypeOf` 函式的用法。  
  
```javascript  
// Create a constructor function.  
function Pasta(grain, width) {  
    this.grain = grain;  
    this.width = width;  
}  
// Create an object from the pasta constructor.  
var spaghetti = new Pasta("wheat", 0.2);  
  
// Obtain the prototype from the object.  
var proto = Object.getPrototypeOf(spaghetti);  
  
// Add a property to the prototype and validate that  
// the original object has the property.  
proto.foodgroup = "carbohydrates";  
document.write(spaghetti.foodgroup + " ");  
  
// Verify that the prototype obtained from the object  
// is the same as the prototype of the constructor.  
var result = (proto === Pasta.prototype);  
document.write(result + " ");  
  
// Verify that prototype obtained from the object  
// is a prototype of the original object.  
var result = proto.isPrototypeOf(spaghetti);  
document.write(result);  
  
// Output: carbohydrates true true  
```  
  
## 範例  
 下列範例會使用 `Object.getPrototypeOf` 函式驗證資料型別。  
  
```javascript  
var reg = /a/;  
var result = (Object.getPrototypeOf(reg) === RegExp.prototype);  
document.write(result + " ");  
  
var err = new Error("an error");  
var result = (Object.getPrototypeOf(err) === Error.prototype);  
document.write(result);  
  
// Output: true true  
  
```  
  
## 需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 請參閱  
 [prototype 屬性 \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)   
 [isPrototypeOf 方法 \(Object\)](../../javascript/reference/isprototypeof-method-object-javascript.md)