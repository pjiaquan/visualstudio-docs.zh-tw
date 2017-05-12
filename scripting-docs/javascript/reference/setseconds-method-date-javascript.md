---
title: "setSeconds 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "setSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "seconds 方法"
  - "setSeconds 方法"
ms.assetid: 986ffa54-1db6-4af2-ab8b-8353f64f0b57
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# setSeconds 方法 (日期) (JavaScript)
利用本地時間設定 `Date` 物件中的秒數值。  
  
## 語法  
  
```  
  
dateObj  
.setSeconds(  
numSeconds[, numMilli])   
```  
  
## 參數  
 `dateObj`  
 必要項。  任何 `Date` 物件。  
  
 *numSeconds*  
 必要項。  等於秒數值的數值。  
  
 `numMilli`  
 選擇項。  等於毫秒值的數值。  
  
## 備註  
 如果不指定選擇性引數，則所有需要選擇性引數的 **set** 方法都會使用對應的 **get** 方法所傳回的值。  例如，如果未指定 `numMilli` 引數，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 就會使用 **getMilliseconds** 方法所傳回的值。  
  
 若要利用全球定位時間 \(UTC\) 設定秒鐘值，請使用 `setUTCSeconds` 方法。  
  
 如果引數值大於其範圍或者是負數的話，其他的儲存值都會跟著修改。  例如，儲存的日期如果是 "Jan 5, 1996 00:00:00"，這時若呼叫 **setSeconds\(150\)**，則日期會變成 "Jan 5, 1996 00:02:30"。  
  
 `setHours` 方法可以用來設定小時、分鐘、秒和毫秒。  
  
## 範例  
 在下列範例中，說明了如何使用 `setSeconds` 方法。  
  
```javascript  
function SetSecondsDemo(nsec){  
   var d = new Date();         //Create Date object.  
   d.setSeconds(nsec);         //Set seconds.  
   var s = "Current setting is ";  
   s += d.toLocaleString();  
   return(s);                  //Return new setting.  
}  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getSeconds 方法 \(日期\)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [getUTCSeconds 方法 \(日期\)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setUTCSeconds 方法 \(日期\)](../../javascript/reference/setutcseconds-method-date-javascript.md)