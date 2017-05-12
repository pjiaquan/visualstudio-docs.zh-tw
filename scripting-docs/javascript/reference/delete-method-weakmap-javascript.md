---
title: "delete 方法 (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: 7d54ae55-e514-45ba-b403-d1eee46837d2
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# delete 方法 (WeakMap) (JavaScript)
從 `WeakMap` 物件移除指定的項目。  
  
## 語法  
  
```javascript  
weakmapObj.delete(key)  
```  
  
#### 參數  
 `weakmapObj`  
 必要項。  `WeakMap` 物件。  
  
 `key`  
 必要項。  要移除之項目的名稱。  
  
## 屬性值\/傳回值  
 如果項目已經移除，則為 `true`。  
  
## 範例  
 下列範例將示範如何將成員加入至 `WeakMap`，然後刪除成員。  
  
```javascript  
function Dog(breed) {  
    this.breed = breed;  
}  
  
var dog = new Dog("yorkie");  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.delete(dog);  
```  
  
## 需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]