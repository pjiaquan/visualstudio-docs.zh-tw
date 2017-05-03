---
title: "toTimeString 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "toTimeString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toTimeString 方法"
ms.assetid: a4a8c0f2-55a9-4e84-94c3-f0a547fb04b5
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toTimeString 方法 (日期) (JavaScript)
傳回時間的字串值。  
  
## 語法  
  
```  
  
objDate. toTimeString( )  
```  
  
## 備註  
 必要的 `objDate` 參考是 `Date` 物件。  
  
 `toTimeString` 方法會傳回字串值，其中包含目前時區的時間。  
  
## 範例  
 在下列範例中，時間設定為 1970 年 1 月 1 日午夜 \(UTC\) 之後的 2000 毫秒，然後寫出此時間。  
  
```javascript  
var aDate = new Date();  
     aDate.setTime(2000);  
     document.write(aDate.toTimeString());  
  
// Output depends on the time in the current time zone.  
  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 請參閱  
 [toDateString 方法 \(日期\)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [toLocaleTimeString 方法 \(日期\)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)