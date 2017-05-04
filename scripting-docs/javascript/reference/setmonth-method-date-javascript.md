---
title: "setMonth 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "setMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Month 方法"
  - "setMonth 方法"
ms.assetid: 4f5be295-d536-46c0-b3a4-ad06457efe82
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# setMonth 方法 (日期) (JavaScript)
利用本地時間設定 `Date` 物件中的月份值。  
  
## 語法  
  
```  
  
dateObj. setMonth(numMonth[, dateVal])   
```  
  
## 參數  
 `dateObj`  
 必要項。  任何 `Date` 物件。  
  
 `numMonth`  
 必要項。  等於月份的數值。  一月份的值為 0，而其他月份值則為相繼的連續值。  
  
 `dateVal`  
 選擇項。  表示月份日期的數值。  如果未提供這個值，將使用呼叫 `getDate` 方法所得的值。  
  
## 備註  
 若要利用「協調世界時」\(Universal Coordinated Time，UTC\) 設定月份值，請使用 `setUTCMonth` 方法。  
  
 如果 `numMonth` 的值大於 11 \(值為 0 表示一月\) 或者是負數的話，儲存的年份會跟著修改。  例如，儲存的日期如果是 "Jan 5, 1996"，這時若呼叫 **setMonth\(14\)**，則日期會變成 "Mar 5, 1997"。  
  
 **setFullYear** 方法可用來設定年、月和日期。  
  
## 範例  
 在下列範例中，說明了如何使用 `setMonth` 方法。  
  
```javascript  
date = new Date('1/1/1990');  
date.setMonth(14);  
document.write(date);  
  
// Output: Fri Mar 1 00:00:00 PST 1991  
// Note that the time zone corresponds to the time zone on the local computer.  
  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getMonth 方法 \(日期\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth 方法 \(日期\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setUTCMonth 方法 \(日期\)](../../javascript/reference/setutcmonth-method-date-javascript.md)