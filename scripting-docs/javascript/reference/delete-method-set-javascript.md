---
title: "delete 方法 (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: 052c409e-10c9-49f2-955d-5ad7e31c14f3
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# delete 方法 (Set) (JavaScript)
從集合移除指定的項目。  
  
## 語法  
  
```javascript  
setObj.delete(value)  
```  
  
#### 參數  
 `setObj`  
 必要項。  `Set` 物件。  
  
 `value`  
 必要項。  要移除的項目。  
  
## 屬性值\/傳回值  
 如果項目已經移除，則為 `true`。  
  
## 範例  
 下列範例將示範如何將成員加入至 `Set`，然後刪除其中一個成員。  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
s.delete("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776,  
```  
  
## 需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]