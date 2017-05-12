---
title: "Map 物件 (JavaScript) | Microsoft Docs"
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
  - "Map"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: a91dbcbe-f58d-41a0-be15-8c9d30020327
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Map 物件 (JavaScript)
索引鍵\/值組的集合。  
  
## 語法  
  
```javascript  
mapObj = new Map()  
```  
  
## 備註  
 集合中的中索引鍵及值可以是任何類型。  如果您使用現有的索引鍵將值加入至集合，則新的值會取代值舊的值。  
  
## 屬性  
 下表列出 `Map` 物件的屬性。  
  
|屬性|描述|  
|--------|--------|  
|[建構函式](../../javascript/reference/constructor-property-map.md)|指定用來建立對應的函式。|  
|[Prototype \- 原型](../../javascript/reference/prototype-property-map.md)|傳回對應的原型參考。|  
|[size](../../javascript/reference/size-property-map-javascript.md)|傳回對應中的項目數。|  
  
## 方法  
 下表列出 `Map` 物件的方法。  
  
|方法|描述|  
|--------|--------|  
|[clear](../../javascript/reference/clear-method-map-javascript.md)|從對應移除所有項目。|  
|[刪除](../../javascript/reference/delete-method-map-javascript.md)|從對應移除指定的項目。|  
|[forEach](../../javascript/reference/foreach-method-map-javascript.md)|針對對應的每一個項目執行指定之動作。|  
|[get](../../javascript/reference/get-method-map-javascript.md)|從對應傳回指定的項目。|  
|[has](../../javascript/reference/has-method-map-javascript.md)|如果對應包含指定之項目，則傳回 `true`。|  
|[set](../../javascript/reference/set-method-map-javascript.md)|將新項目加入至對應。|  
|[toString](../../javascript/reference/tostring-method-map-javascript.md)|傳回對應的字串表示。|  
|[valueOf](../../javascript/reference/valueof-method-map-javascript.md)|傳回指定物件的原始值。|  
  
## 範例  
 下列範例示範如何將成員加入至 `Map`，然後擷取這些成員。  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (item, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## 需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]