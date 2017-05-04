---
title: "setUTCFullYear 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "setUTCFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日期, UTC"
  - "setUTCFullYear 方法"
  - "UTC 日期, 設定"
ms.assetid: e6c51b49-0149-4f9a-aa74-c73c0306f98e
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCFullYear 方法 (日期) (JavaScript)
使用全球定位時間 \(UTC\) 設定 `Date` 物件中的年份值。  
  
## 語法  
  
```  
  
dateObj.setUTCFullYear(numYear[, numMonth[, numDate]])   
```  
  
## 參數  
 `dateObj`  
 必要項。  任何 `Date` 物件。  
  
 `numYear`  
 必要項。  等於年份的數值。  
  
 `numMonth`  
 選擇項。  等於月份的數值。  一月份的值為 0，而其他月份值則為相繼的連續值。  如果提供 *numDate*，就必須提供此引數。  
  
 *numDate*  
 選擇項。  等於月份日期的數值。  
  
## 備註  
 如果不指定選擇性引數，則所有需要選擇性引數的 **set** 方法都會使用對應的 **get** 方法所傳回的值。  例如，如果 `numMonth` 引數未指定，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 就會使用從 `getUTCMonth` 方法所傳回的值。  
  
 此外，如果引數值大於其範圍或者是負數，其他的儲存值都會跟著修改。  
  
 若要利用本地時間設定年份，請使用 `setFullYear` 方法。  
  
 `Date` 物件支援的年份範圍大約可以涵蓋 1970 年前後各約 285,616 年。  
  
## 範例  
 在下列範例中，說明了如何使用 `setUTCFullYear` 方法。  
  
```javascript  
var dtFirst = new Date();  
dtFirst.setUTCFullYear(2007);  
  
var dtSecond = new Date();  
// 10 is the value for November.   
dtSecond.setUTCFullYear(2008, 10, 3);   
  
document.write (dtFirst.toUTCString());  
document.write ("<br />");  
document.write (dtSecond.toUTCString());  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getFullYear 方法 \(日期\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear 方法 \(日期\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear 方法 \(日期\)](../../javascript/reference/setfullyear-method-date-javascript.md)