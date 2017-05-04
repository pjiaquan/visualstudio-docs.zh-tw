---
title: "toJSON 方法 (日期) (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "toJSON 方法"
ms.assetid: f91df030-e9c9-425e-8e6d-b46bdda66cb6
caps.latest.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 27
---
# toJSON 方法 (日期) (JavaScript)
由 [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md) 方法用來轉換物件的資料，以便進行 JavaScript 物件標記法 \(JSON\) 序列化。  
  
## 語法  
  
```  
  
objectname.toJSON()  
```  
  
## 參數  
 `objectname`  
 必要項。  需要 JSON 序列化的物件。  
  
## 備註  
 `toJSON` 方法是由 `JSON.stringify` 函式所使用。  `JSON.stringify` 會將 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 值序列化為 JSON 文字。  如果 `toJSON` 方法提供給 `JSON.stringify`，則當呼叫 `JSON.stringify` 時也會呼叫 `toJSON` 方法。  
  
 `toJSON` 方法是 [Date](../../javascript/reference/date-object-javascript.md)[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 物件的內建成員。  它會針對 UTC 時區 \(以後置字元 Z 表示\) 傳回 ISO 格式的日期字串。  
  
 您可以覆寫 `Date` 型別的 `toJSON` 方法，或針對其他物件型別定義 `toJSON` 方法，以便在 JSON 序列化之前轉換特定物件型別的資料。  
  
## 範例  
 下列範例會使用 `toJSON` 方法，以大寫序列化字串成員值。  當呼叫 `JSON.stringify` 時，便會呼叫 `toJSON` 方法。  
  
```javascript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
  
/* The value of jsonText is:  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## 範例  
 下列範例說明如何使用 `toJSON` 方法，此方法是 [Date](../../javascript/reference/date-object-javascript.md) 物件的內建成員。  
  
```javascript  
var dt = new Date('8/24/2009');  
dt.setUTCHours(7, 30, 0);  
var jsonText = JSON.stringify(dt);  
  
/* The value of jsonText is:  
'"2009-08-24T07:30:00Z"'  
*/  
```  
  
## 需求  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)] **適用於：** [Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [JSON 物件](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse 函式](../../javascript/reference/json-parse-function-javascript.md)   
 [JSON.stringify 函式](../../javascript/reference/json-stringify-function-javascript.md)   
 [JavaScript 方法](../../javascript/reference/javascript-methods.md)