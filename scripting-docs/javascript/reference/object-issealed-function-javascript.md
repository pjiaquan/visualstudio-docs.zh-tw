---
title: "Object.isSealed 函式 (JavaScript) | Microsoft Docs"
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
  - "isSealed 函式 [JavaScript]"
  - "Object.isSealed [JavaScript]"
  - "屬性 [JavaScript], 鎖定屬性"
ms.assetid: af4f192e-cebe-44b9-8eef-90c096f5ae8f
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Object.isSealed 函式 (JavaScript)
如果現有屬性 \(Property\) 的屬性 \(Attribute\) 無法在物件中修改，而且新的屬性 \(Property\) 無法加入至物件，則會傳回 `true`。  
  
## 語法  
  
```javascript  
Object.isSealed(object)  
```  
  
#### 參數  
 `object`  
 必要項。  要測試的物件。  
  
## 傳回值  
 如果下列兩個條件都成立，則為 `true`：  
  
-   此物件無法擴充，這表示新的屬性無法加入至物件。  
  
-   對於所有現有的屬性 \(Property\) 而言，`configurable` 屬性 \(Attribute\) 都是 `false`。  
  
 如果物件沒有任何屬性，此函式會在物件無法擴充時傳回 `true`。  
  
## 例外狀況  
 如果 `object` 不是物件，就會擲回 `TypeError` 例外狀況。  
  
## 備註  
 當某個屬性 \(Property\) 的 `configurable` 屬性 \(Attribute\) 為 `false` 時，此屬性 \(Property\) 的屬性 \(Attribute\) 無法變更，而且無法刪除此屬性 \(Property\)。  當 `writable` 為 `false` 時，無法變更資料屬性值。  當 `configurable` 為 `false` 且 `writable` 為 `true` 時，可以變更 `value` 和 `writable` 屬性。  
  
 `Object.isSealed` 函式不會使用屬性 \(Property\) 的 `writable` 屬性 \(Attribute\) 來判斷它的傳回值。  
  
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
|`Object.isSealed`|否|是|否|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|否|是|是|  
  
## 範例  
 以下範例說明 `Object.isSealed` 函式的用法。  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Seal the object, and verify that it is sealed.  
Object.seal(obj);  
document.write(Object.isSealed(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write(obj.newProp);  
document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
  
// Output:  
// true  
// undefined  
// 10  
  
```  
  
## 需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 請參閱  
 [Object.preventExtensions 函式](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.seal 函式](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze 函式](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible 函式](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isFrozen 函式](../../javascript/reference/object-isfrozen-function-javascript.md)   
 [Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.getOwnPropertyDescriptor 函式](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)