---
title: "setUTCDate 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "setUTCDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日期, 設定"
  - "日期, UTC"
  - "setUTCDate 方法"
  - "UTC 日期, 設定"
ms.assetid: e6c3b876-70fe-4103-b197-6c84c078ce10
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# setUTCDate 方法 (日期) (JavaScript)
使用全球定位時間 \(UTC\) 設定 `Date` 物件中的數字月份日期。  
  
## 語法  
  
```  
  
dateObj.setUTCDate(numDate)   
```  
  
## 參數  
 `dateObj`  
 必要項。  任何 `Date` 物件。  
  
 *numDate*  
 必要項。  等於月份日期的數值。  
  
## 備註  
 若要使用當地時間設定月份日期，請使用 `setDate` 方法。  
  
 如果 *numDate* 的值大於 **Date** 物件中所儲存之月份的天數，或者是負數的話，日期將會設成等於 *numDate* 減去所儲存之月份的天數。  例如，如果儲存的日期是 1996 年 1 月 5 日，而且有呼叫 **setUTCDate\(32\)**，日期就會變更為 1996 年 2 月 1 日。  負數的處理方式類似。  
  
 **setUTCFullYear** 方法可用來設定年、月和日期。  
  
## 範例  
 在下列範例中，說明了如何使用 `setUTCDate` 方法。  
  
```javascript  
function SetUTCDateDemo(newdayofmonth){  
   var d = new Date();           // Create Date object.  
   d.setUTCDate(newdayofmonth);  // Set UTC day of month.  
   var s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                    // Return new setting.  
}  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getDate 方法 \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [getUTCDate 方法 \(Date\)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [setDate 方法 \(Date\)](../../javascript/reference/setdate-method-date-javascript.md)