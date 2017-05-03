---
title: "Object.getOwnPropertyNames 函式 (JavaScript) | Microsoft Docs"
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
  - "getOwnPropertyNames 方法 [JavaScript]"
  - "Object.getOwnPropertyNames 方法 [JavaScript]"
ms.assetid: 59f4b6b1-02be-44b3-a06c-a5ca8f70c3d8
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Object.getOwnPropertyNames 函式 (JavaScript)
傳回物件之擁有屬性的名稱。  物件的擁有屬性是指在該物件上直接定義的屬性，而且不是從物件的原型繼承而來的屬性。  物件的屬性包含欄位 \(物件\) 和函式。  
  
## 語法  
  
```javascript  
Object.getOwnPropertyNames(object)  
```  
  
#### 參數  
  
|參數|定義|  
|--------|--------|  
|`object`|必要項。  包含擁有屬性的物件。|  
  
## 傳回值  
 包含物件之擁有屬性名稱的陣列。  
  
## 例外狀況  
 如果為 `object` 引數提供的值並不是物件的名稱，則會擲回 `TypeError` 例外狀況。  
  
## 備註  
 `getOwnPropertyNames` 方法會傳回可列舉和不可列舉之屬性和方法的名稱。  如果只要傳回可列舉之屬性和方法的名稱，您可以使用 [Object.keys 函式](../../javascript/reference/object-keys-function-javascript.md)。  
  
## 範例  
 下列範例會建立具有三個屬性和方法的物件。  然後會使用 `getOwnPropertyNames` 方法取得物件的擁有屬性 \(包括此方法\)。  
  
```javascript  
function Pasta(grain, width, shape) {  
    // Define properties.  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Get the own property names.  
var arr = Object.getOwnPropertyNames(spaghetti);  
document.write (arr);  
  
// Output:  
//   grain,width,shape,toString  
```  
  
## 範例  
 下列範例會顯示以 Pasta 建構函式建構的 spaghetti 物件中，以 's' 字母開頭的屬性名稱。  
  
```javascript  
function Pasta(grain, size, shape) {  
    this.grain = grain;   
    this.size = size;   
    this.shape = shape;   
}  
  
var spaghetti = new Pasta("wheat", 2, "circle");  
  
var names = Object.getOwnPropertyNames(spaghetti).filter(CheckKey);  
document.write(names);   
  
// Check whether the first character of a string is 's'.   
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);   
    if (firstChar.toLowerCase() == 's')  
        return true;   
    else  
         return false;   
}  
// Output:  
// size,shape  
```  
  
## 需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 請參閱  
 [Object.keys 函式](../../javascript/reference/object-keys-function-javascript.md)