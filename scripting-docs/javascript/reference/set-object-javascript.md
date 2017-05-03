---
title: "Set 物件 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Set"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4a4dd749-2a76-44fb-9cb0-a3ef317f75fb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Set 物件 (JavaScript)
可以是任何類型的唯一值集合。  
  
## 語法  
  
```  
setObj = new Set()  
  
```  
  
## 備註  
 當您嘗試將非唯一的值加入至 `Set`，新值不會加入至集合。  
  
## 屬性  
 下表列出 `Set` 物件的屬性。  
  
|屬性|描述|  
|--------|--------|  
|[建構函式](../../javascript/reference/constructor-property-set.md)|指定用來建立集合的函式。|  
|[Prototype \- 原型](../../javascript/reference/prototype-property-set.md)|傳回集合的原型參考。|  
|[size](../../javascript/reference/size-property-set-javascript.md)|傳回集合中項目的數目。|  
  
## 方法  
 下表列出 `Set` 物件的方法。  
  
|方法|描述|  
|--------|--------|  
|[新增](../../javascript/reference/add-method-set-javascript.md)|將項目加入至集合。|  
|[clear](../../javascript/reference/clear-method-set-javascript.md)|從資料集移除所有項目。|  
|[刪除](../../javascript/reference/delete-method-set-javascript.md)|從集合移除指定的項目。|  
|[forEach](../../javascript/reference/foreach-method-set-javascript.md)|針對集合的每一個項目執行指定之動作。|  
|[has](../../javascript/reference/has-method-set-javascript.md)|如果集合包含指定之項目，則傳回 `true`。|  
|[toString](../../javascript/reference/tostring-method-set-javascript.md)|傳回集合的字串表示。|  
|[valueOf](../../javascript/reference/valueof-method-set-javascript.md)|傳回指定物件的原始值。|  
  
## 範例  
 下列範例將示範如何將成員加入至集合，然後擷取這些成員。  
  
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