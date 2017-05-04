---
title: "setMilliseconds 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "setMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "毫秒"
  - "setMilliseconds 方法"
ms.assetid: 6c398961-130e-4f60-802f-6c30e1ef4de4
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setMilliseconds 方法 (日期) (JavaScript)
利用本地時間設定 `Date` 物件中的毫秒值。  
  
## 語法  
  
```  
  
dateObj.  
setMilliseconds(  
numMilli  
)   
```  
  
## 參數  
 `dateObj`  
 必要項。  任何 `Date` 物件。  
  
 `numMilli`  
 必要項。  等於毫秒值的數值。  
  
## 備註  
 若要利用全球定位時間 \(UTC\) 設定毫秒值，請使用 `setUTCMilliseconds` 方法。  
  
 如果 `numMilli` 的值大於 999 或者是負數的話，儲存的秒數會適量遞增 \(如果必要的話，還會同時遞增分鐘、小時等等\)。  
  
## 範例  
 在下列範例中，說明了如何使用 `setMilliseconds` 方法。  
  
```javascript  
function SetMSecDemo(nmsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setMilliseconds(nmsec);    // Set milliseconds.  
   s = "Current setting is ";  
   s += d.toLocaleString();  
   s += " and " + d.getMilliseconds();  
   s += " milliseconds";  
   return(s);                   // Return new date setting.  
}  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getMilliseconds 方法 \(日期\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [getUTCMilliseconds 方法 \(日期\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds 方法 \(日期\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)