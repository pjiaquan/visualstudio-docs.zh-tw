---
title: "setMinutes 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "setMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "分鐘"
  - "setMinutes 方法"
ms.assetid: 34c959cd-cd29-4cee-8e04-9061cf6d42f3
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setMinutes 方法 (日期) (JavaScript)
利用本地時間設定 **Date** 物件的分鐘值。  
  
## 語法  
  
```  
  
dateObj.setMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## 參數  
 `dateObj`  
 必要項。  任何 `Date` 物件。  
  
 `numMinutes`  
 必要項。  等於分鐘值的數值。  如果使用下列任何一個引數，就必須提供此引數。  
  
 *numSeconds*  
 選擇項。  等於秒數值的數值。  如果使用 `numMilli` 引數，就必須一併提供這個引數。  
  
 `numMilli`  
 選擇項。  等於毫秒值的數值。  
  
## 備註  
 如果不指定選擇性引數，則所有需要選擇性引數的 **set** 方法都會使用對應的 **get** 方法所傳回的值。  例如，如果未指定 *numSeconds* 引數，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 就會使用 `getSeconds` 方法傳回的值。  
  
 若要利用「協調世界時」\(Universal Coordinated Time，UTC\) 設定分鐘值，請使用 `setUTCMinutes` 方法。  
  
 如果引數值大於其範圍或者是負數的話，其他的儲存值都會跟著修改。  例如，儲存的日期如果是 "Jan 5, 1996 00:00:00"，這時若呼叫 **setMinutes\(90\)**，則日期會變成 "Jan 5, 1996 01:30:00"。 負數的處理方式類似。  
  
## 範例  
 在下列範例中，說明了如何使用 `setMinutes` 方法。  
  
```javascript  
function SetMinutesDemo(nmin, nsec){  
   var d, s;                     // Declare variables.  
   d = new Date();               // Create Date object.  
   d.setMinutes(nmin, nsec);     // Set minutes.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    // Return new setting.  
}  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getMinutes 方法 \(日期\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [getUTCMinutes 方法 \(日期\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setUTCMinutes 方法 \(日期\)](../../javascript/reference/setutcminutes-method-date-javascript.md)