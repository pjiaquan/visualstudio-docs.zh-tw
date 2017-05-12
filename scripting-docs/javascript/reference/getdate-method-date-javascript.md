---
title: "getDate 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "getDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date 物件"
  - "日期，傳回當月日期"
  - "getDate 方法"
ms.assetid: 67e7f07c-dd46-4b42-82d6-e53e4bd33703
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# getDate 方法 (日期) (JavaScript)
利用本地時間取得月份日期。  
  
## 語法  
  
```  
  
dateObj.getDate()   
```  
  
#### 參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## 傳回值  
 介於 1 和 31 之間的整數，表示月份日期。  
  
## 備註  
 若要利用全球定位時間 \(UTC\) 取得月份日期，請使用 `getUTCDate` 方法。  
  
## 範例  
 在下列範例中，說明了如何使用 `getDate` 方法。  
  
```javascript  
var date = new Date("Jan 01, 2001");  
var str = "Today's date is: ";  
   str += (date.getMonth() + 1) + "/";  
   str += date.getDate() + "/";  
   str += date.getFullYear();  
document.write(str);  
  
// Output: Today's date is: 1/1/2001  
  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getUTCDate 方法 \(Date\)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [setDate 方法 \(Date\)](../../javascript/reference/setdate-method-date-javascript.md)   
 [setUTCDate 方法 \(日期\)](../../javascript/reference/setutcdate-method-date-javascript.md)