---
title: "delete 方法 (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: 19e93366-7d42-4abf-b7b9-fcf943fa17a3
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# delete 方法 (WeakSet) (JavaScript)
將指定的項目從 `WeakSet` 中移除。  
  
## 語法  
  
```javascript  
weaksetObj.delete(obj)  
```  
  
#### 參數  
 `weaksetObj`  
 必要項。  `WeakSet` 物件。  
  
 `obj`  
 必要項。  要移除的項目。  
  
## 屬性值\/傳回值  
 如果已移除項目，則為 `true`。  
  
## 範例  
 下列範例示範如何加入和刪除 `WeakSet` 的項目。  
  
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