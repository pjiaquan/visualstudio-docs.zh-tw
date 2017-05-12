---
title: "add 方法 (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: d35d0287-6b33-4720-b9d7-8954c428ce4e
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# add 方法 (WeakSet) (JavaScript)
將新項目加入 `WeakSet`。  
  
## 語法  
  
```javascript  
weaksetObj.add(obj)  
```  
  
#### 參數  
 `weaksetObj`  
 必要項。  `WeakSet` 物件。  
  
 `obj`  
 必要項。  `WeakSet` 的新項目。  
  
## 備註  
 新項目必須是物件 \(而不是任意值\)，而且必須是唯一的。  如果您將非唯一的項目加入至 `WeakSet`，新項目不會加入至集合 \(Collection\)。  
  
## 範例  
 下列範例示範如何將成員加入集合，然後檢查是否已加入這些成員。  
  
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