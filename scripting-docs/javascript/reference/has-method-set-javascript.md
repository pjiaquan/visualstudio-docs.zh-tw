---
title: "has 方法 (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: fb80f2e0-fc5e-4508-af14-1c3b3b833636
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# has 方法 (Set) (JavaScript)
如果集合包含指定之項目，則傳回 `true`。  
  
## 語法  
  
```javascript  
setObj.has(value)  
```  
  
#### 參數  
 `setObj`  
 必要項。  `Set` 物件。  
  
 `value`  
 必要項。  要測試的項目。  
  
## 屬性值\/傳回值  
 如果集合包含指定之項目，則為 `true`。  
  
## 範例  
 下列範例顯示如何將成員加入至 `Set`，然後檢查此集合是否包含特定成員。  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
  
document.write(s.has(1776));  
document.write(s.has("1776"));  
  
// Output:  
// true  
// false  
  
```  
  
## 需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]