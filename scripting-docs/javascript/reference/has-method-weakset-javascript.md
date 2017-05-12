---
title: "has 方法 (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: e24f0876-26bd-4007-b12a-360bb6fa0951
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# has 方法 (WeakSet) (JavaScript)
如果 `WeakSet` 包含指定的項目，則傳回 `true`。  
  
## 語法  
  
```javascript  
setObj.has(obj)  
```  
  
#### 參數  
 `setObj`  
 必要項。  `WeakSet` 物件。  
  
 `obj`  
 必要項。  要測試的項目。  
  
## 屬性值\/傳回值  
 如果集合包含指定的項目，則為 `true`。  
  
## 範例  
 下列範例示範如何將成員加入 `WeakSet`，然後檢查集合是否包含特定成員。  
  
```javascript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
  
```  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]