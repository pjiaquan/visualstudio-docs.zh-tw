---
title: "setHours 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "setHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日期, 設定"
  - "小時"
  - "setHours 方法"
ms.assetid: 460f742d-f8d2-4874-9d07-2fb969fef066
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# setHours 方法 (日期) (JavaScript)
利用本地時間設定 `Date` 物件中的小時值。  
  
## 語法  
  
```  
  
dateObj.setHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## 參數  
 `dateObj`  
 必要項。  任何 `Date` 物件。  
  
 `numHours`  
 必要項。  等於小時值的數值。  
  
 `numMin`  
 選擇項。  等於分鐘值的數值。  如果使用下列任何一個引數，就必須提供此引數。  
  
 `numSec`  
 選擇項。  等於秒數值的數值。  如果使用下列引數，就必須一併提供這個引數。  
  
 `numMilli`  
 選擇項。  等於毫秒值的數值。  
  
## 備註  
 如果不指定選擇性引數，則所有需要選擇性引數的 **set** 方法都會使用對應的 **get** 方法所傳回的值。  例如，如果未指定 `numMinutes` 引數，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 就會使用 `getMinutes` 方法傳回的值。  
  
 若要利用「協調世界時」\(Universal Coordinated Time，UTC\) 設定小時值，請使用 `setUTCHours` 方法。  
  
 如果引數值大於其範圍或者是負數的話，其他的儲存值都會跟著修改。  例如，儲存的日期如果是 "Jan 5, 1996 00:00:00"，這時若呼叫 **setHours\(30\)**，則日期會變成 "Jan 6, 1996 06:00:00"。 負數的處理方式類似。  
  
## 範例  
 在下列範例中，說明了如何使用 `setHours` 方法。  
  
```javascript  
function SetHoursDemo(nhr, nmin, nsec){  
   var d, s;                     //Declare variables.  
   d = new Date();               //Create Date object.  
   d.setHours(nhr, nmin, nsec);  //Set hours, minutes, & seconds.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    //Return new date setting.  
}  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getHours 方法 \(日期\)](../../javascript/reference/gethours-method-date-javascript.md)   
 [getUTCHours 方法 \(日期\)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setUTCHours 方法 \(日期\)](../../javascript/reference/setutchours-method-date-javascript.md)