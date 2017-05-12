---
title: "add 方法 (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: b4eea447-fd5b-4380-978e-1b95f6dbc438
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# add 方法 (Set) (JavaScript)
將新項目加入至集合 \(Set\)。  
  
## 語法  
  
```javascript  
setObj.add(value)  
```  
  
#### 參數  
 `setObj`  
 必要項。  `Set` 物件。  
  
 `value`  
 必要項。  `Set` 的新項目。  
  
## 備註  
 新項目可以是任何類型，而且必須是唯一的。  如果您將非唯一的項目加入至 `Set`，新項目不會加入至集合 \(Collection\)。  
  
## 範例  
 下面範例會示範如何將成員加入至集合 \(Set\)，然後擷取這些成員。  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## 需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]