---
title: "Proxy 物件 (JavaScript) | Microsoft Docs"
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
ms.assetid: 2b89abee-04fa-47e6-9676-980016cff5f8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Proxy 物件 (JavaScript)
啟用物件的自訂行為。  
  
## 語法  
  
```  
proxyObj = new Proxy(target, handler)  
```  
  
#### 參數  
 `target`  
 必要項。  Proxy 所要虛擬化的物件或函式。  
  
 `handler`  
 必要項。  使用方法 \(設陷\) 來實作自訂行為的物件。  
  
## 備註  
 `Proxy` 物件可用來攔截另一個物件上的內部低階作業。  Proxy 物件可用於攔截、物件虛擬化、記錄\/分析和其他用途。  
  
 如果未在 Proxy 的處理常式中定義特定作業的設陷，作業會轉送至目標。  
  
 事件處理常式物件會定義下列方法 \(設陷\)，來實作自訂行為。  此處的範例並不詳盡。  若要支援處理常式方法中的條件式預設行為，請使用 [Reflect 物件](../../javascript/reference/reflect-object-javascript.md) 的方法。  
  
|處理常式方法 \(設陷\) 語法|使用範例|  
|----------------------|----------|  
|`apply: function(target, thisArg, args)`|函式呼叫的設陷。|  
|`construct: function(target, args)`|建構函式的設陷。|  
|`defineProperty: function(target, propertyName, descriptor)`|[Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md) 的設陷。|  
|`deleteProperty: function(target, propertyName)`|`delete` 陳述式的設陷。|  
|`enumerate: function(target)`|[for…in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) 陳述式、[Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md)、[Object.keys](../../javascript/reference/object-keys-function-javascript.md) 函式和 [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md) 的設陷。|  
|`get: function(target, propertyName, receiver)`|任何 [getter](../../javascript/creating-objects-javascript.md) 屬性的設陷。|  
|`getOwnPropertyDescriptor: function(target, propertyName)`|[Object.getOwnPropertyDescriptor 函式](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md) 的設陷。|  
|`getPrototypeOf: function(target)`|[Object.getPrototypeOf 函式](../../javascript/reference/object-getprototypeof-function-javascript.md) 的設陷。|  
|`has: function(target, propertyName)`|`in` 運算子、[hasOwnProperty 方法 \(Object\)](../../javascript/reference/hasownproperty-method-object-javascript.md) 和其他方法的設陷。|  
|`isExtensible: function(target)`|[Object.isExtensible 函式](../../javascript/reference/object-isextensible-function-javascript.md) 的設陷。|  
|`ownKeys: function(target)`|[Object.getOwnPropertyNames 函式](../../javascript/reference/object-getownpropertynames-function-javascript.md) 的設陷。|  
|`preventExtensions: function(target)`|[Object.preventExtensions 函式](../../javascript/reference/object-preventextensions-function-javascript.md) 的設陷。|  
|`set: function(target, propertyName, value, receiver)`|任何 [setter](../../javascript/creating-objects-javascript.md) 屬性的設陷。|  
|`setPrototypeOf: function(target, prototype)`|[Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md) 的設陷。|  
  
## 範例  
 下列程式碼範例示範如何使用 `get` 設陷建立物件常值的 Proxy。  
  
```javascript  
var target = {};  
var handler = {  
  get: function (receiver, name) {  
    // This example includes a template string.  
    return `Hello, ${name}!`;  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(p.world);  
  
// Output:  
// Hello, world!  
  
```  
  
## 範例  
 下列程式碼範例示範如何使用 `apply` 設陷建立函式的 Proxy。  
  
```javascript  
var target = function () { return 'I am the target'; };  
var handler = {  
  // This example includes a rest parameter.  
  apply: function (receiver, ...args) {  
    return 'I am the proxy';  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(target()):  
console.log(p()):  
  
// Output:  
// I am the target  
// I am the proxy  
```  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]