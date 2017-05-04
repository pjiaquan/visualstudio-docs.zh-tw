---
title: "Object 物件 (JavaScript) | Microsoft Docs"
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
  - "object"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Object 物件"
ms.assetid: d24ef8fc-217b-4828-94e1-19f72780bae0
caps.latest.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 25
---
# Object 物件 (JavaScript)
提供所有 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 物件通用的功能。  
  
## 語法  
  
```  
  
obj  
 = new Object([value])   
```  
  
## 參數  
 `obj`  
 必要項。  `Object` 物件指派目標的變數名稱。  
  
 *值*  
 選擇項。  任何一個 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 基本資料類型 \(數字、布林值或字串\)。  如果值是物件，則會傳回未修改的物件。  如果值是 `null`、**未定義**，或未提供，則會建立沒有內容的物件。  
  
## 備註  
 `Object` 物件包含在所有其他 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 物件中，其方法和屬性會都可用於所有其他物件。  方法可以在使用者定義物件中重新定義，且由 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 在適當的時間呼叫。  **ToString** 方法是經常重新定義的 `Object` 方法範例。  
  
 在這個語言參考中，每個 `Object` 方法的描述都包含內建 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 物件的預設和物件特定的實作資訊。  
  
## 需求  
 `Object Object` 是在 [!INCLUDE[jsv3text](../../javascript/reference/includes/jsv3text-md.md)] 引入。  下列清單中的某些成員是在較新版本中引入。  
  
## 屬性  
 以下資料表列出 `Object Object` 的屬性。  
  
|屬性|描述|  
|--------|--------|  
|[\_\_proto\_\_ 屬性](../../javascript/reference/proto-property-object-javascript.md)|指定物件的原型。|  
|[constructor 屬性](../../javascript/reference/constructor-property-object-javascript.md)|指定建立物件的函式。|  
|[prototype 屬性](../../javascript/reference/prototype-property-object-javascript.md)|傳回物件類別的原型參考。|  
  
## 函式  
 以下資料表列出 `Object Object` 的函式。  
  
|函式|描述|  
|--------|--------|  
|[Object.assign 函式](../../javascript/reference/object-assign-function-object-javascript.md)|將值從一或多個來源物件複製到目標物件。|  
|[Object.create 函式](../../javascript/reference/object-create-function-javascript.md)|建立具有指定原型，並選擇性地包含指定屬性的物件。|  
|[Object.defineProperties 函式](../../javascript/reference/object-defineproperties-function-javascript.md)|將一或多個屬性加入至物件，及\/或修改現有屬性 \(Property\) 的屬性 \(Attribute\)。|  
|[Object.defineProperty 函式](../../javascript/reference/object-defineproperty-function-javascript.md)|將屬性加入至物件，或修改現有屬性 \(Property\) 的屬性 \(Attribute\)。|  
|[Object.freeze 函式](../../javascript/reference/object-freeze-function-javascript.md)|防止修改現有屬性 \(Property\) 的屬性 \(Attribute\) 和值，並可防止新屬性 \(Property\) 加入。|  
|[Object.getOwnPropertyDescriptor 函式](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)|傳回資料屬性或存取子屬性的定義。|  
|[Object.getOwnPropertyNames 函式](../../javascript/reference/object-getownpropertynames-function-javascript.md)|傳回物件的屬性和方法的名稱。|  
|[Object.getOwnPropertySymbols 函式](../../javascript/reference/object-getownpropertysymbols-function-javascript.md)|傳回物件的符號屬性。|  
|[Object.getPrototypeOf 函式](../../javascript/reference/object-getprototypeof-function-javascript.md)|傳回物件的原型。|  
|[Object.is 函式](../../javascript/reference/object-is-function-javascript.md)|傳回值，這個值表示兩個值是否相同。|  
|[Object.isExtensible 函式](../../javascript/reference/object-isextensible-function-javascript.md)|傳回表示是否可以將新屬性加入物件的值。|  
|[Object.isFrozen 函式](../../javascript/reference/object-isfrozen-function-javascript.md)|如果無法在物件中修改現有屬性的屬性和值，且新的屬性無法加入物件，便傳回 `true`。|  
|[Object.isSealed 函式](../../javascript/reference/object-issealed-function-javascript.md)|如果無法在物件中修改現有屬性 \(Property\) 的屬性 \(Attribute\)，且新的屬性 \(Property\) 無法加入物件，便傳回 `true`。|  
|[Object.keys 函式](../../javascript/reference/object-keys-function-javascript.md)|傳回可列舉屬性的名稱和物件的方法。|  
|[Object.preventExtensions 函式](../../javascript/reference/object-preventextensions-function-javascript.md)|防止新屬性加入物件。|  
|[Object.seal 函式](../../javascript/reference/object-seal-function-javascript.md)|防止修改現有屬性 \(Property\) 的屬性 \(Attribute\)，並可防止新屬性  \(Attribute\) 加入。|  
|[Object.setPrototypeOf 函式](../../javascript/reference/object-setprototypeof-function-javascript.md)|設定物件的原型。|  
  
## 方法  
 以下資料表列出 `Object Object` 的方法。  
  
|方法|描述|  
|--------|--------|  
|[hasOwnProperty 方法](../../javascript/reference/hasownproperty-method-object-javascript.md)|傳回布林值，表示物件是否具有指定名稱的屬性。|  
|[isPrototypeOf 方法](../../javascript/reference/isprototypeof-method-object-javascript.md)|傳回布林值，表示物件是否存在於另一個物件的原型階層。|  
|[propertyIsEnumerable 方法](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|傳回布林值，表示指定的屬性是否為物件的一部分，以及是否可列舉。|  
|[toLocaleString 方法](../../javascript/reference/tolocalestring-method-object-javascript.md)|傳回依據目前的地區設定轉換成字串的物件。|  
|[toString 方法](../../javascript/reference/tostring-method-object-javascript.md)|傳回物件的字串表示。|  
|[valueOf 方法](../../javascript/reference/valueof-method-object-javascript.md)|傳回指定物件的基本值。|  
  
## 請參閱  
 [JavaScript 物件](../../javascript/reference/javascript-objects.md)