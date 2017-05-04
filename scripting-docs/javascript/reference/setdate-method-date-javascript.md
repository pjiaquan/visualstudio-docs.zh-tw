---
title: "setDate 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "setDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "setDate 方法"
  - "日期，設定"
ms.assetid: a84b9b01-a6d0-489f-8a13-e7af9e9630b2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# setDate 方法 (日期) (JavaScript)
利用本地時間設定， `Date` 物件的數值日期的月份值。  
  
## 語法  
  
```  
  
dateObj.setDate(numDate)   
```  
  
## 參數  
 `dateObj`  
 必要項。  任意 `Date` 物件。  
  
 `numDate`  
 必要項。  等於月份日期的數值。  
  
## 備註  
 若要設定這個日期的月份值使用通用協調的時間 \(UTC\)，使用 `setUTCDate` 方法。  
  
 如果 `numDate` 的值大於中的天數大於在月份，則日期會變成給以後的月份和年份。  例如，在中，儲存的日期如果是 `setDate(32)` 1 月 5 日，這時若呼叫， 1996 年至 1996 年 2 月 1 日的日期變更。  如果 `numDate` 是負數的話，日期復原為舊版的月份和年份。  例如，在中，儲存的日期如果是 `setDate(-32)` 1 月 5 日，這時若呼叫， 1996 年至 1995 年 11 月 29 日的日期變更。  
  
 [setFullYear 方法 \(日期\)](../../javascript/reference/setfullyear-method-date-javascript.md) 可用於設定年、月和日。  
  
## 範例  
 下列範例示範如何使用 `setDate` 方法。  
  
```javascript  
var date = new Date("12/15/1990");  
date.setDate(30);  
document.write(date);  
  
// Output (for the PST time zone): Sun Dec 30 00:00:00 PST 1990  
  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getDate 方法 \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [setFullYear 方法 \(日期\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setMonth 方法 \(日期\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCDate 方法 \(日期\)](../../javascript/reference/setutcdate-method-date-javascript.md)