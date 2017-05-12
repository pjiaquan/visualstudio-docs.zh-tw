---
title: "setUTCMonth 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "setUTCMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日期, UTC"
  - "Month 方法"
  - "setUTCMonth 方法"
  - "UTC 日期, 設定"
ms.assetid: cdac5f64-c4fd-44cc-ba3a-9a8dd3dd3fad
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCMonth 方法 (日期) (JavaScript)
使用全球定位時間 \(UTC\) 設定 `Date` 物件中的月份值。  
  
## 語法  
  
```  
  
dateObj.setUTCMonth(numMonth[, dateVal])   
```  
  
## 參數  
 `dateObj`  
 必要項。  任何 `Date` 物件。  
  
 `numMonth`  
 必要項。  等於月份的數值。  一月份的值為 0，而其他月份值則為相繼的連續值。  
  
 `dateVal`  
 選擇項。  表示月份日期的數值。  如果未提供的話，將使用呼叫 `getUTCDate` 方法所得的值。  
  
## 備註  
 若要利用本地時間設定月份值，請使用 `setMonth` 方法。  
  
 如果 `numMonth` 的值大於 11 \(一月是月份 0\) 或者是負數，儲存的年份會跟著適量遞增或遞減。  例如，儲存的日期如果是 "Jan 5, 1996 00:00:00.00"，這時若呼叫 **setUTCMonth\(14\)**，則日期會變成 "Mar 5, 1997 00:00:00.00"。  
  
 **setUTCFullYear** 方法可用來設定年、月和日期。  
  
## 範例  
 在下列範例中，說明了如何使用 `setUTCMonth` 方法。  
  
```javascript  
function SetUTCMonthDemo(newmonth){  
   var d, s;                       // Declare variables.  
   d = new Date();                 // Create Date object.  
   d.setUTCMonth(newmonth);        // Set UTC month.  
   s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                      // Return new setting.  
}  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getMonth 方法 \(日期\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth 方法 \(日期\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth 方法 \(日期\)](../../javascript/reference/setmonth-method-date-javascript.md)