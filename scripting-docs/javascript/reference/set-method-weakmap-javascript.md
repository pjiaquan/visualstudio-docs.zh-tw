---
title: "set 方法 (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: 29fc72b1-224f-4f19-8c06-5d926d695b03
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# set 方法 (WeakMap) (JavaScript)
將新項目加入至 `WeakMap` 物件。  
  
## 語法  
  
```javascript  
weakmapObj.set(key, value)  
```  
  
#### 參數  
 `weakmapObj`  
 必要項。  `WeakMap` 物件。  
  
 `key`  
 必要項。  物件，表示要加入之項目的索引鍵。  這個項目必須是物件參考。  
  
 `value`  
 必要項。  要加入的項目的值。  
  
## 屬性值\/傳回值  
 會傳回包含新索引鍵\/值組的 `WeakMap` 物件。  
  
## 備註  
 如果您使用現有的索引鍵將某個值加入至集合，則新的值會取代舊的值。  
  
## 範例  
 下面範例會示範如何將成員加入至 `WeakMap` 物件。  
  
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
```  
  
## 需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]