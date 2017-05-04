---
title: "Object.isFrozen 函式 (JavaScript) | Microsoft Docs"
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
  - "isFrozen 函式 [JavaScript]"
  - "Object.isFrozen 函式 [JavaScript]"
ms.assetid: 6cf1bbc6-56e8-429b-8e2c-0024fa614acc
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Object.isFrozen 函式 (JavaScript)
如果現有屬性 \(Property\) 的屬性 \(Attribute\) 和值無法在物件中修改，而且新的屬性 \(Property\) 無法加入至物件，則會傳回 `true`。  
  
## 語法  
  
```javascript  
Object.isFrozen(object)  
```  
  
#### 參數  
 `object`  
 必要項。  要測試的物件。  
  
## 傳回值  
 如果下列所有條件都成立則為 `true`：  
  
-   此物件無法擴充，這表示新的屬性無法加入至物件。  
  
-   對於所有現有的屬性 \(Property\) 而言，`configurable` 屬性 \(Attribute\) 都是 `false`。  
  
-   對於所有現有的資料屬性 \(Property\) 而言，`writable` 屬性 \(Attribute\) 都是 `false`。  
  
 如果物件沒有現有的屬性，此函式會在物件無法擴充時傳回 `true`。  
  
## 例外狀況  
 如果 `object` 不是物件，就會擲回 `TypeError` 例外狀況。  
  
## 備註  
 當某個屬性 \(Property\) 的 `configurable` 屬性 \(Attribute\) 為 `false` 時，此屬性 \(Property\) 的屬性 \(Attribute\) 無法變更，而且無法刪除此屬性 \(Property\)。  當 `writable` 為 `false` 時，無法變更資料屬性值。  當 `configurable` 為 `false` 且 `writable` 為 `true` 時，可以變更 `value` 和 `writable` 屬性。  
  
 如需如何設定屬性 \(Property\) 的屬性 \(Attribute\) 的詳細資訊，請參閱 [Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md)。  若要取得屬性 \(Property\) 的屬性 \(Attribute\)，您可以使用 [Object.getOwnPropertyDescriptor 函式](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)。  
  
## 相關函式  
 以下相關函式可防止修改物件屬性。  
  
|函式|物件設為無法擴充|`configurable` 針對每個屬性設定為 `false`|`writable` 針對每個屬性設定為 `false`|  
|--------|--------------|--------------------------------------|----------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|是|否|否|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|是|是|否|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|是|是|是|  
  
 如果下表中所有標記的條件都成立，則下列函式會傳回 `true`。  
  
|函式|物件可擴充嗎？|所有屬性的 `configurable` 都是 `false` 嗎？|所有資料屬性的 `writable` 都是 `false` 嗎？|  
|--------|-------------|----------------------------------------|--------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|是|否|否|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|否|是|否|  
|`Object.isFrozen`|否|是|是|  
  
## 範例  
 以下範例說明 `Object.isFrozen` 函式的用法。  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object, and verify that it is frozen.  
Object.freeze(obj);  
document.write(obj.isFrozen());  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write (obj.newProp);  
document.write ("<br/>");  
  
// Try to delete a property, and then verify that it is still present.  
delete obj.length;  
document.write (obj.length);  
document.write ("<br/> ");  
  
// Try to change a property value, and then verify that it is not changed.  
obj.pasta = "linguini";  
document.write (obj.pasta);  
  
// Output:  
// true  
// undefined  
// 10  
// spaghetti  
  
```  
  
## 需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 請參閱  
 [Object.preventExtensions 函式](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.seal 函式](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze 函式](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible 函式](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed 函式](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.getOwnPropertyDescriptor 函式](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames 函式](../../javascript/reference/object-getownpropertynames-function-javascript.md)