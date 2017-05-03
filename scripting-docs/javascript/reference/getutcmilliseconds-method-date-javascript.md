---
title: "getUTCMilliseconds 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "getUTCMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "毫秒"
  - "UTC 時間，傳回"
  - "getUTCMilliseconds 方法"
ms.assetid: 7491d387-7b6a-40df-89e5-55c64795ef70
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCMilliseconds 方法 (日期) (JavaScript)
使用全球定位時間 \(UTC\)，取得 `Date` 物件的毫秒數。  
  
## 語法  
  
```  
  
dateObj.getUTCMilliseconds()   
```  
  
#### 參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## 傳回值  
 傳回可以介於的毫秒值。  
  
## 備註  
 若要取得毫秒數當地時間，請使用 `getMilliseconds` 方法。  
  
## 範例  
 在下列程式碼中，說明了如何使用 `getUTCMilliseconds` 方法。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(34);  
document.writedate.getUTCMilliseconds());  
  
// Output:  
// 0   
// 34   
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getMilliseconds 方法 \(日期\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [setMilliseconds 方法 \(日期\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds 方法 \(日期\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)