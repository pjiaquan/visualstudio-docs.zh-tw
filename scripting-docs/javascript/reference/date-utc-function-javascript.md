---
title: "Date.UTC 函式 (JavaScript) | Microsoft Docs"
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
  - "UTC"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "UTC 函式 [JavaScript]"
  - "UTC 日期，傳回"
  - "Date.UTC 函式 [JavaScript]"
ms.assetid: c0d67ce1-a47e-4dfd-bbf4-21619c406a0f
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Date.UTC 函式 (JavaScript)
傳回全球定位時間 \(UTC\) \(或 GMT\) 1970 年 1 月 1 日午夜開始到指定日期之間的毫秒數。  
  
## 語法  
  
```  
Date.UTC(year, month, day[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## 參數  
 `year`  
 必要項。  為了世紀交替時的日期能夠正確，必須指定完整的年份。  如果 `year` 介於 0 到 99 之間，則 `year` 是假設為 1900 \+ `year`。  
  
 `month`  
 必要項。  代表月份，以 0 到 11 之間的整數表示一月到十二月。  
  
 `day`  
 必要項。  代表日期，以介於 1 到 31 之間的整數表示。  
  
 `hours`  
 選擇項。  如果提供 `minutes`，就必須提供此引數。  以 0 到 23 之間的整數 \(表示午夜到下午 11 點\) 來指定小時。  
  
 `minutes`  
 選擇項。  如果提供 `seconds`，就必須提供此引數。  以 0 到 59 之間的整數來指定分鐘。  
  
 `seconds`  
 選擇項。  如果提供 `milliseconds`，就必須提供此引數。  以 0 到 59 之間的整數來指定秒數。  
  
 `ms`  
 選擇項。  以 0 到 999 之間的整數來指定毫秒數。  
  
## 備註  
 `Date.UTC` 函式會傳回 UTC 1970 年 1 月 1 日午夜開始到提供之日期之間的毫秒數。  此傳回值可用於 `setTime` 方法及 `Date` 物件建構函式中。  如果引數值大於其範圍或者是負數的話，其他的儲存值都會跟著修改。  例如，您若指定 150 秒，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 就會重新將該數字定義為 2 分 30 秒。  
  
 `Date.UTC` 函式與接受日期的 `Date` 物件建構函式之間的差別在於：`Date.UTC` 函式採用的是 UTC，而 `Date` 物件建構函式則採用本地時間。  
  
## 範例  
 以下範例說明 `Date.UTC` 函式的用法。  
  
```javascript  
// Determine the milliseconds per day.  
 var MinMilli = 1000 * 60;  
var HrMilli = MinMilli * 60;  
var DyMilli = HrMilli * 24;  
  
var date = new Date("June 1, 1990");  
var year = date.getFullYear();  
var month = date.getMonth();  
var day = date.getDay();  
  
var newDay = new Date("January 16, 2020");  
var yeartoday = newDay.getUTCFullYear();  
var monthtoday = newDay.getUTCMonth();  
var dayofmonthtoday = newDay.getUTCDate();  
  
// Get the milliseconds since 1/1/1970 UTC.  
var t1 = Date.UTC(year, month - 1, day)  
var t2 = Date.UTC(yeartoday, monthtoday, dayofmonthtoday);  
  
// Determine the difference in days.  
var days = (t2 - t1) / DyMilli;  
  
document.write(days);  
// Output: 10848  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [setTime 方法 \(日期\)](../../javascript/reference/settime-method-date-javascript.md)