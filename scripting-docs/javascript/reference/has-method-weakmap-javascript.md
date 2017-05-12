---
title: "has 方法 (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: 12bedca1-bde7-413a-a4e2-06c03559044f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# has 方法 (WeakMap) (JavaScript)
如果 `WeakMap` 物件包含指定的項目，則傳回 `true`。  
  
## 語法  
  
```javascript  
weakmapObj.has(key)  
```  
  
#### 參數  
 `weakmapObj`  
 必要項。  `WeakMap` 物件。  
  
 `key`  
 必要項。  要測試之元素的索引鍵。  
  
## 屬性值\/傳回值  
 如果 `WeakMap` 包含指定的索引鍵，則為 `true`。  
  
## 範例  
 下列範例示範如何將成員加入至 `WeakMap`，然後使用 `has` 檢查該成員是否存在。  
  
```javascript  
var dog = {  
    breed: "yorkie"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
  
document.write(wm.has(dog));  
  
// Output:  
// true  
```  
  
## 需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]