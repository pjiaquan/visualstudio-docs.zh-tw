---
title: "getSeconds 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "getSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "seconds 方法"
  - "GetSeconds 方法"
ms.assetid: 97b10674-af0b-4681-a846-38f972196501
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# getSeconds 方法 (日期) (JavaScript)
利用本地時間取得， `Date` 物件的秒鐘。  
  
## 語法  
  
```  
  
dateObj.getSeconds()   
```  
  
#### 參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## 傳回值  
 傳回介於 0 和 59 之間的整數。  當的時間不足一秒當要進入目前這一分鐘的時間時，會傳回零。  如果 `Date` 建立物件，但沒有指定時間，預設的秒值設定為 0。  
  
## 備註  
 若要取得值使用通用協調時間的秒 \(UTC\)，使用 `getUTCSeconds` 方法。  
  
## 範例  
 下列範例示範如何使用 `getSeconds` 方法。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getSeconds());  
document.write("<br/>");  
  
date.setSeconds(5);  
document.write(date.getSeconds());  
  
// Output:  
// 0  
// 5  
  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**: [Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getUTCSeconds 方法 \(日期\)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setSeconds 方法 \(日期\)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds 方法 \(日期\)](../../javascript/reference/setutcseconds-method-date-javascript.md)