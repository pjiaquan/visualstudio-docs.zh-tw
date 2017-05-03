---
title: "setUTCMilliseconds 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "setUTCMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日期, UTC"
  - "毫秒"
  - "setUTCMilliseconds 方法"
  - "UTC 時間, 設定"
ms.assetid: ed8e4486-d4b2-4b73-836b-dd1d3bb991a0
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCMilliseconds 方法 (日期) (JavaScript)
利用全球定位時間 \(UTC\) 設定 `Date` 物件中的毫秒值。  
  
## 語法  
  
```  
  
dateObj.setUTCMilliseconds(numMilli)   
```  
  
## 參數  
 `dateObj`  
 必要項。  任何 `Date` 物件。  
  
 `numMilli`  
 必要項。  等於毫秒值的數值。  
  
## 備註  
 若要利用本地時間設定毫秒，請使用 `setMilliseconds` 方法。  
  
 如果 `numMilli` 的值大於 999 或者是負數的話，儲存的秒數會適量遞增 \(如果必要的話，還會同時遞增分鐘、小時等等\)。  
  
## 範例  
 在下列範例中，說明了如何使用 `setUTCMilliseconds` 方法。  
  
```javascript  
function SetUTCMSecDemo(nmsec){     
// Create Date object.  
   var d = new Date();             
// Set UTC milliseconds.  
   d.setUTCMilliseconds(nmsec);    
  
   var s = "Current setting is ";  
   s += d.toUTCString();  
   s += " and " + d.getUTCMilliseconds();  
   s += " milliseconds"  
   return(s);  
}  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getMilliseconds 方法 \(日期\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [getUTCMilliseconds 方法 \(日期\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setMilliseconds 方法 \(日期\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)