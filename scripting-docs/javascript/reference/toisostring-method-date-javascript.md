---
title: "toISOString 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "toISOString 方法 [JavaScript]"
ms.assetid: 58577d8f-3ae8-4887-8687-26233ea79ff6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# toISOString 方法 (日期) (JavaScript)
傳回日期的 ISO 格式字串值。  
  
## 語法  
  
```javascript  
  
objDate.toISOString()  
```  
  
## 傳回值  
 日期的字串表示法，以國際標準組織 \(ISO\) 格式表示。  
  
## 例外狀況  
 如果 `objDate` 不包含有效的日期，便會擲回 `RangeError` 例外狀況。  
  
## 備註  
 此 ISO 格式是 ISO 8601 格式的簡化。  如需詳細資訊，請參閱[日期和時間字串](../../javascript/date-and-time-strings-javascript.md)。  
  
 時區一定是 UTC，以輸出的尾碼 Z 表示。  
  
## 範例  
 在下列範例中，說明了如何使用 `toISOString` 方法。  
  
```javascript  
var dt = new Date("30 July 2010 15:05 UTC");  
document.write(dt.toISOString());  
document.write("<br />");  
document.write(dt.toUTCString());  
  
// Output:  
//  2010-07-30T15:05:00.000Z  
//  Fri, 30 Jul 2010 15:05:00 UTC  
  
```  
  
## 需求  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 請參閱  
 [Date 物件](../../javascript/reference/date-object-javascript.md)   
 [日期和時間字串](../../javascript/date-and-time-strings-javascript.md)