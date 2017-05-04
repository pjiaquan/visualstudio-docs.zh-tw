---
title: "Object.create 函式 (JavaScript) | Microsoft Docs"
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
  - "create 函式 [JavaScript]"
  - "Object.create 函式 [JavaScript]"
ms.assetid: 0ad31f36-a9ee-444e-b0fe-c87843d03196
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Object.create 函式 (JavaScript)
建立具有指定之原型且選擇性包含指定之屬性的物件。  
  
## 語法  
  
```  
Object.create(prototype, descriptors)  
```  
  
#### 參數  
 `prototype`  
 必要項。  要當做原型使用的物件。  可能是 `null`。  
  
 `descriptors`  
 選擇項。  包含一個或多個屬性描述元的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 物件。  
  
 「*資料屬性*」\(Data Property\) 是可以取得並設定其值的屬性。  資料屬性 \(Property\) 描述元包含 `value` 屬性 \(Attribute\)，以及 `writable`、`enumerable` 和 `configurable` 屬性 \(Attribute\)。  如果未指定最後三個屬性，則會預設為 `false`。  每當擷取或設定值時，「*存取子屬性*」\(Accessor Property\) 都會呼叫使用者提供的函式。  存取子屬性 \(Property\) 描述元包含 `set` 屬性 \(Attribute\) 或 `get` 屬性 \(Attribute\)，或兩者都包含。  如需詳細資訊，請參閱[Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md)。  
  
## 傳回值  
 具有指定之內部原型且包含指定之屬性 \(如果有的話\) 的新物件。  
  
## 例外狀況  
 如果下列任何一個條件成立，就會擲回 `TypeError` 例外狀況：  
  
-   `prototype` 引數既不是物件也不是 `null`。  
  
-   `descriptors` 引數中的描述元含有 `value` 或 `writable` 屬性，並且含有 `get` 或 `set` 屬性。  
  
-   `descriptors` 引數中的描述元包含不是函式的 `get` 或 `set` 屬性。  
  
## 備註  
 您可以使用這個函式並搭配 `null` `prototype` 參數以停止原型鏈結，  建立的物件就沒有原型。  
  
## 範例  
 下列範例會使用 `null` 原型建立物件，並加入兩個 enumerable 屬性。  
  
```javascript  
var newObj = Object.create(null, {  
            size: {  
                value: "large",  
                enumerable: true  
            },  
            shape: {  
                value: "round",  
                enumerable: true  
            }  
        });  
  
document.write(newObj.size + "<br/>");  
document.write(newObj.shape + "<br/>");  
document.write(Object.getPrototypeOf(newObj));  
  
// Output:  
// large  
// round  
// null  
  
```  
  
## 範例  
 下列範例會建立與 Object 物件具有相同內部原型的物件。  您可以看見它和使用物件常值常值建立的物件有相同的原型。  [Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md) 函式會取得原始物件的原型。  若要取得物件的屬性描述元，您可以使用 [Object.getOwnPropertyDescriptor 函式](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。  
  
```javascript  
var firstLine = { x: undefined, y: undefined };  
  
var secondLine = Object.create(Object.prototype, {  
        x: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            },  
            y: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            }  
});  
  
document.write("first line prototype = " + Object.getPrototypeOf(firstLine));  
document.write("<br/>");  
document.write("second line prototype = " + Object.getPrototypeOf(secondLine));  
  
// Output:  
// first line prototype = [object Object]  
// second line prototype = [object Object]  
```  
  
## 範例  
 下列範例會建立與 Shape 物件具有相同內部原型的物件。  
  
```javascript  
  
// Create the shape object.  
var Shape = { twoDimensional: true, color: undefined, hasLineSegments: undefined };  
  
var Square = Object.create(Object.getPrototypeOf(Shape));  
  
```  
  
## 需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 請參閱  
 [Object.getPrototypeOf 函式](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [isPrototypeOf 方法 \(Object\)](../../javascript/reference/isprototypeof-method-object-javascript.md)   
 [建立物件](../../javascript/creating-objects-javascript.md)