---
title: "WeakMap 物件 (JavaScript) | Microsoft Docs"
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
  - "WeakMap"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4682d2dc-caf9-4fa8-8313-a0a0b804fd1d
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# WeakMap 物件 (JavaScript)
索引鍵\/值組的集合，其中的每個索引鍵都是物件參考。  
  
## 語法  
  
```  
weakmapObj = new WeakMap()  
```  
  
## 備註  
 您無法列舉 `WeakMap` 物件。  
  
 如果您使用現有的索引鍵將值加入至集合，則新的值會取代值舊的值。  
  
 在 `WeakMap` 物件中，索引鍵物件的參考是以「弱式」方式保存。  這表示 `WeakMap` 不會阻止對索引鍵物件進行記憶體回收。  沒有索引鍵物件的參考 \(而非 `WeakMap`\) 時，記憶體回收行程可能會回收索引鍵物件。  
  
## 屬性  
 下表列出 `WeakMap` 物件的屬性。  
  
|屬性|描述|  
|--------|--------|  
|[建構函式](../../javascript/reference/constructor-property-weakmap.md)|指定用來建立 `WeakMap` 的函式。|  
|[Prototype \- 原型](../../javascript/reference/prototype-property-weakmap.md)|傳回 `WeakMap` 的原型參考。|  
  
## 方法  
 下表列出 `WeakMap` 物件的方法。  
  
|方法|描述|  
|--------|--------|  
|[clear](../../javascript/reference/clear-method-weakmap-javascript.md)|將所有項目從 `WeakMap` 移除。|  
|[刪除](../../javascript/reference/delete-method-weakmap-javascript.md)|從 `WeakMap` 移除指定的項目。|  
|[get](../../javascript/reference/get-method-weakmap-javascript.md)|從 `WeakMap` 傳回指定的項目。|  
|[has](../../javascript/reference/has-method-weakmap-javascript.md)|如果 `WeakMap` 包含指定之項目，則傳回 `true`。|  
|[set](../../javascript/reference/set-method-weakmap-javascript.md)|將新項目加入至 `WeakMap`。|  
|[toString](../../javascript/reference/tostring-method-weakmap-javascript.md)|傳回 `WeakMap` 的字串表示。|  
|[valueOf](../../javascript/reference/valueof-method-weakmap-javascript.md)|傳回指定物件的原始值。|  
  
## 範例  
 下列範例將示範如何將成員加入至 `WeakMap` 物件，然後擷取這些成員。  
  
```javascript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## 需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]