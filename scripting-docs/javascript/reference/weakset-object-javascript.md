---
title: "WeakSet 物件 (JavaScript) | Microsoft Docs"
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
ms.assetid: f97e6e7c-d678-4e32-978e-d949a7cafa3a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# WeakSet 物件 (JavaScript)
可屬於任何類型的唯一物件集合。  
  
## 語法  
  
```  
setObj = new WeakSet()  
```  
  
## 備註  
 如果您嘗試將非唯一的物件加入 `WeakSet`，新物件不會加入集合 \(Collection\)。  
  
 不同於 `Set`，只有物件可以加入集合 \(Collection\)。  無法將任意值加入集合 \(Collection\)。  
  
 在 `WeakSet` 物件中，會以較「弱」的方式來保留集合 \(Set\) 中的物件參考。  這表示 `WeakSet` 不會防止物件發生記憶體回收。  當沒有物件參考時 \(`WeakSet` 除外\)，記憶體回收行程可能會回收物件。  
  
 `WeakSet` \(或 `WeakMap`\) 在需要快取物件或物件中繼資料的一些情節下可能會很有用。  例如，非可延伸物件的中繼資料可能儲存在 `WeakSet` 中，或者您可能使用 `WeakSet` 建立使用者影像的快取。  
  
## 屬性  
 下表列出 `WeakSet` 物件的屬性。  
  
|屬性|描述|  
|--------|--------|  
|建構函式|指定用來建立集合的函式。|  
|原型|傳回集合的原型參考。|  
  
## 方法  
 下表列出 `WeakSet` 物件的方法。  
  
|方法|描述|  
|--------|--------|  
|加入|將項目加入集合。|  
|刪除|將指定的項目從集合中移除。|  
|has|如果集合包含指定的項目，則傳回 `true`。|  
  
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