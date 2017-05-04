---
title: "set 方法 (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: 31ee71a0-b09d-442a-9e02-825accf94ffa
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# set 方法 (Map) (JavaScript)
將新項目加入至對應。  
  
## 語法  
  
```javascript  
mapObj.set(key, value)  
```  
  
#### 參數  
 `mapObj`  
 必要項。  `Map` 物件。  
  
 `key`  
 必要項。  新項目的索引鍵。  
  
 `value`  
 必要項。  要加入的項目的值。  
  
## 屬性值\/傳回值  
 會傳回包含新索引鍵\/值組的 `Map` 物件。  
  
## 備註  
 如果您使用現有的索引鍵將某個值加入至集合，則新的值會取代舊的值。  
  
## 範例  
 下面範例會示範如何將成員加入至 `Map`，然後擷取這些成員。  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// black  
// red  
// 2  
```  
  
## 需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]