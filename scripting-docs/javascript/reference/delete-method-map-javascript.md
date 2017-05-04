---
title: "delete 方法 (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: a073e1a1-5862-485b-b2bd-26c66a3aff51
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# delete 方法 (Map) (JavaScript)
從對應移除指定的項目。  
  
## 語法  
  
```javascript  
mapObj.delete(key)  
```  
  
#### 參數  
 `mapObj`  
 必要項。  `Map` 物件。  
  
 `key`  
 必要項。  要移除之項目的名稱。  
  
## 屬性值\/傳回值  
 如果項目已經移除，則為 `true`。  
  
## 範例  
 下列範例將示範如何將成員加入至 `Map`，然後刪除其中一個成員。  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.delete(1);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// red  
// 2  
```  
  
## 需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]