---
title: "setUTCMinutes 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "setUTCMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日期, UTC"
  - "分鐘"
  - "setUTCMinutes 方法"
  - "UTC 時間, 設定"
ms.assetid: 2415e788-6d28-46dd-a103-0931a1fd1446
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCMinutes 方法 (日期) (JavaScript)
使用「協調世界時」\(Coordinated Universal Time，UTC\) 設定 `Date` 物件中的分鐘值。  
  
## 語法  
  
```  
  
dateObj.setUTCMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## 參數  
 `dateObj`  
 必要項。  任何 `Date` 物件。  
  
 `numMinutes`  
 必要項。  等於分鐘值的數值。  如果使用下列任何一個引數，就必須提供此引數。  
  
 *numSeconds*  
 選擇項。  等於秒數值的數值。  如果使用 `numMilli` 的話，就必須指定這一項。  
  
 `numMilli`  
 選擇項。  等於毫秒值的數值。  
  
## 備註  
 如果不指定選擇性引數，則所有需要選擇性引數的 **set** 方法都會使用對應的 **get** 方法所傳回的值。  例如，如果未指定 *numSeconds* 引數，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 就會使用 `getUTCSeconds` 方法所傳回的值。  
  
 若要利用本地時間修改分鐘值，請使用 `setMinutes` 方法。  
  
 如果引數值大於其範圍或者是負數的話，其他的儲存值都會跟著修改。  例如，儲存的日期如果是 "Jan 5, 1996 00:00:00.00"，這時若呼叫 **setUTCMinutes\(70\)**，則日期會變成 "Jan 5, 1996 01:10:00.00"。  
  
 **setUTCHours** 方法可以用來設定小時、分鐘、秒和毫秒。  
  
## 範例  
 在下列範例中，說明了如何使用 `setUTCMinutes` 方法：  
  
```javascript  
function SetUTCMinutesDemo(nmin, nsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setUTCMinutes(nmin,nsec);  // Set UTC minutes.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                   // Return new setting.  
}  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getMinutes 方法 \(日期\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [getUTCMinutes 方法 \(日期\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setMinutes 方法 \(日期\)](../../javascript/reference/setminutes-method-date-javascript.md)