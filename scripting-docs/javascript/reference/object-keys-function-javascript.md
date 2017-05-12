---
title: "Object.keys 函式 (JavaScript) | Microsoft Docs"
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
  - "keys 方法 [JavaScript]"
  - "Object.keys 方法 [JavaScript]"
ms.assetid: cf4a7daf-cf28-4467-bc6b-f7f106ec3876
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Object.keys 函式 (JavaScript)
傳回可列舉之屬性的名稱和物件的方法。  
  
## 語法  
  
```javascript  
Object.keys(object)  
```  
  
#### 參數  
  
|參數|定義|  
|--------|--------|  
|`object`|必要項。  包含屬性和方法的物件。  這可以是您建立的物件或現有的文件物件模型 \(DOM\) 物件。|  
  
## 傳回值  
 包含物件之可列舉屬性和方法名稱的陣列。  
  
## 例外狀況  
 如果為 `object` 引數提供的值並不是物件的名稱，則會擲回 `TypeError` 例外狀況。  
  
## 備註  
 `keys` 方法只會傳回可列舉屬性和方法的名稱。  若要傳回可列舉和不可列舉之屬性和方法的名稱，可以使用 [Object.getOwnPropertyNames 函式](../../javascript/reference/object-getownpropertynames-function-javascript.md)。  
  
 如需屬性 \(Property\) 之 `enumerable` 屬性 \(Attribute\) 的詳細資訊，請參閱 [Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md) 和 [Object.getOwnPropertyDescriptor 函式](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。  
  
## 範例  
 下列範例會建立具有三個屬性和方法的物件。  然後它會使用 `keys` 方法取得物件的屬性和方法。  
  
```javascript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
  
    // Define a method.  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Put the enumerable properties and methods of the object in an array.  
var arr = Object.keys(spaghetti);  
document.write (arr);  
  
// Output:  
// grain,width,shape,toString  
```  
  
## 範例  
 下列範例會顯示 Pasta 物件中開頭字母為 "g" 的所有可列舉屬性名稱。  
  
```javascript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
}  
  
var polenta = new Pasta("corn", 1, "mush");  
  
var keys = Object.keys(polenta).filter(CheckKey);  
document.write(keys);  
  
// Check whether the first character of a string is "g".  
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);  
    if (firstChar.toLowerCase() == "g")  
        return true;  
    else  
        return false;  
}  
  
// Output:  
// grain  
```  
  
## 需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 請參閱  
 [Object.getOwnPropertyNames 函式](../../javascript/reference/object-getownpropertynames-function-javascript.md)