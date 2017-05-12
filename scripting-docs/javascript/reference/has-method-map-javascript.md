---
title: "has 方法 (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: 876df854-2941-4db2-92c6-1b497840b169
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# has 方法 (Map) (JavaScript)
如果對應包含指定之項目，則傳回 `true`。  
  
## 語法  
  
```javascript  
mapObj.has(key)  
```  
  
#### 參數  
 `mapObj`  
 必要項。  `Map` 物件。  
  
 `key`  
 必要項。  要測試之元素的索引鍵。  
  
## 屬性值\/傳回值  
 如果對應包含指定之項目，則為 `true`。  
  
## 範例  
 下列範例示範如何將成員加入至 `Map`，然後檢查對應是否包含該成員。  
  
```javascript  
var m = new Map();  
m.set(2, "red");  
  
document.write(m.has(2));  
  
// Output:  
// true  
```  
  
## 需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]