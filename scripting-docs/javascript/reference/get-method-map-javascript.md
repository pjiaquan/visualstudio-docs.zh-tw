---
title: "get 方法 (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: bebbd6bc-6e61-4674-8196-7e907798973f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# get 方法 (Map) (JavaScript)
從對應傳回指定的項目。  
  
## 語法  
  
```javascript  
mapObj.get(key)  
```  
  
#### 參數  
 `mapObj`  
 必要項。  `Map` 物件。  
  
 `key`  
 必要項。  `Map` 中之項目的索引鍵。  
  
## 屬性值\/傳回值  
 傳回與這個索引鍵相關聯的物件。  如果 `Map` 不包含索引鍵，這個方法會傳回 `undefined` 值。  
  
## 範例  
 下列範例示範如何從 `Map` 物件擷取項目。  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
document.write(m.get(2));  
  
// Output:  
// red  
  
```  
  
## 需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]