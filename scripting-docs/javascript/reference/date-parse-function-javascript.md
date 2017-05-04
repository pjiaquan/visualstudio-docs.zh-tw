---
title: "Date.parse 函式 (JavaScript) | Microsoft Docs"
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
  - "parse"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date.parse 函式 [JavaScript]"
  - "parse 函式 [JavaScript]"
ms.assetid: ed737e50-6398-4462-8779-2af3c03f8325
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Date.parse 函式 (JavaScript)
剖析包含日期的字串，然後傳回該日期與 1970 年 1 月 1 日午夜之間的毫秒數。  
  
## 語法  
  
```  
Date.parse(dateVal)   
```  
  
## 備註  
 必要的 `dateVal` 引數是包含日期的字串，或是從 ActiveX 物件或其他物件中擷取的 VT\_DATE 值。  如需 `Date.parse` 函式可以剖析之日期字串的詳細資訊，請參閱[日期和時間字串](../../javascript/date-and-time-strings-javascript.md)。  
  
 `Date.parse` 函式會傳回整數值，表示從 1970 年 1 月 1 日午夜開始到 `dateVal` 中提供之日期之間的毫秒數。  
  
## 範例  
 以下範例說明 `Date.parse` 函式的用法：  
  
```javascript  
var dateString = "November 1, 1997 10:15 AM";  
var mSec = Date.parse(dateString);  
document.write(mSec);  
// Output: 878404500000  
```  
  
## 範例  
 下列範例會傳回提供的日期與 1\/1\/1970 之間的差異。  
  
```javascript  
var minMilli = 1000 * 60;  
var hrMilli = minMilli * 60;  
var dyMilli = hrMilli * 24;  
  
var testDate = new Date("June 1, 1990");  
var ms = Date.parse(testDate);  
var days = Math.round(ms / dyMilli);  
  
var dateStr = "";  
dateStr += "There are " + days + " days ";  
dateStr += "between 01/01/1970 and " + testDate;  
document.write(dateStr);  
  
// Output: There are 7456 days between 01/01/1970 and Fri Jun 1 00:00:00 PDT 1990  
  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [getDate 方法 \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)