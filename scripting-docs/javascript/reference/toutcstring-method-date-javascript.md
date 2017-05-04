---
title: "toUTCString 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "toUTCString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toUTCString 方法"
  - "UTC 日期, 轉換為字串"
ms.assetid: eb0983ed-7884-42fa-a2cc-de92b3111207
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toUTCString 方法 (日期) (JavaScript)
傳回利用全球定位時間 \(UTC\) 轉換為字串的日期。  
  
## 語法  
  
```  
  
dateObj.toUTCString()   
```  
  
## 備註  
 必要的 `dateObj` 參考是任何 `Date` 物件。  
  
 `toUTCString` 方法會以簡單易讀的格式傳回使用 UTC 規格設定格式的 `String` 物件。  
  
## 範例  
 在下列範例中，說明了如何使用 `toUTCString` 方法。  
  
```javascript  
function toUTCStrDemo(){  
   var d, s;                   //Declare variables.  
   d = new Date();             //Create Date object.  
   s = "Current setting is ";  
   s += d.toUTCString();       //Convert to UTC string.  
   return(s);                  //Return UTC string.  
}  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [toGMTString 方法 \(日期\)](../../javascript/reference/togmtstring-method-date-javascript.md)