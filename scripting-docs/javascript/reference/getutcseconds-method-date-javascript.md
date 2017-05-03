---
title: "getUTCSeconds 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "getUTCSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "UTC 時間，傳回"
  - "seconds 方法"
  - "getUTCSeconds 方法"
ms.assetid: 2d8ea7dc-79f8-4a9b-b2ab-732db2bcd5fd
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCSeconds 方法 (日期) (JavaScript)
使用全球定位時間 \(UTC\)，取得 `Date` 物件的秒數。  
  
## 語法  
  
```  
  
dateObj.getUTCSeconds()   
```  
  
#### 參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## 傳回值  
 傳回介於 0 和 59 之間的整數。  當的時間不足一秒當要進入目前這一分鐘的時間時，會傳回零。  如果 `Date` 建立物件，但沒有指定時間，預設的秒值設定為 0。  
  
## 備註  
 若要取得本地時間的秒數，請使用 `getSeconds` 方法。  
  
## 範例  
 下列範例示範如何使用 `getUTCSeconds` 方法。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date. getUTCSeconds());  
  
// Output: 0  
  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getSeconds 方法 \(日期\)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [setSeconds 方法 \(日期\)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds 方法 \(日期\)](../../javascript/reference/setutcseconds-method-date-javascript.md)