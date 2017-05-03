---
title: "setFullYear 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "setFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Year 方法"
  - "setFullYear 方法"
  - "日期，設定"
ms.assetid: 635e4f5a-0210-4c01-8152-b0da4146f6ff
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# setFullYear 方法 (日期) (JavaScript)
利用本地時間設定， `Date` 物件中的年份。  
  
## 語法  
  
```  
  
dateObj.setFullYear(numYear[, numMonth[, numDate]])   
```  
  
## 參數  
 `dateObj`  
 必要項。  任意 `Date` 物件。  
  
 `numYear`  
 必要項。  單一數值的年份。  
  
 `numMonth`  
 選擇項。  以零起始的數值為月份 \(0 到 12 月年，十一月\)。  必須指定 `numDate` 是否指定。  
  
 `numDate`  
 選擇項。  這個數值相等的資料記錄。  
  
## 備註  
 如果不指定選擇性引數，則所有需要選擇性引數的 **set** 方法都會使用對應的 **get** 方法所傳回的值。  例如， `numMonth` ，如果引數是選擇性的，不過，未指定，會從 **getMonth** 方法所傳回的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 用法。  
  
 此外，在中，如果引數值大於其曆法範圍或者是負數，則日期向前復原適當。  
  
 若要將年份使用通用協調的時間 \(UTC\)，使用 `setUTCFullYear` 方法。  
  
 在 1970 年之前和之後，在日期物件支援的年份範圍大約 285,616 年。  
  
## 範例  
 以下範例說明如何使用 `setFullYear` 方法：  
  
```javascript  
var date1 = new Date("1/1/2001");  
date1.setFullYear(2007);  
  
var date2 = new Date("1/1/2001");  
date2.setFullYear(2008, 10, 3);   
  
document.write (date1.toLocaleString());  
document.write ("<br />");  
document.write (date2.toLocaleString());  
  
// Output:  
// Monday, January 01, 2007 12:00:00 AM  
// Monday, November 03, 2008 12:00:00 AM  
  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getFullYear 方法 \(日期\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear 方法 \(日期\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setUTCFullYear 方法 \(日期\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)