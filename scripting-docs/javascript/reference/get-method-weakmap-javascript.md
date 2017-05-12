---
title: "get 方法 (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: d922c55d-486d-4feb-aedc-1f4867c417d2
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# get 方法 (WeakMap) (JavaScript)
從 `WeakMap` 物件傳回指定的項目。  
  
## 語法  
  
```javascript  
weakmapObj.get(key)  
```  
  
#### 參數  
 `weakmapObj`  
 必要項。  `WeakMap` 物件。  
  
 `key`  
 必要項。  `WeakMap` 中之元素的索引鍵。  
  
## 屬性值\/傳回值  
 傳回與這個索引鍵相關聯的物件。  如果 `WeakMap` 未包含索引鍵，這個方法會傳回 `undefined` 值。  
  
## 範例  
 下列範例示範如何從 `WeakMap` 物件擷取成員。  
  
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