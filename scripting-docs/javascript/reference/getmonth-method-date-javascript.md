---
title: "getMonth 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "getMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date 物件"
  - "日期，月份值"
  - "Month 方法"
  - "GetMonth 方法"
ms.assetid: c20dd8ba-1d78-42f1-8717-ed3dfd2362dd
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# getMonth 方法 (日期) (JavaScript)
利用本地時間取得月份。  
  
## 語法  
  
```  
  
dateObj.getMonth()   
```  
  
#### 參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## 傳回值  
 `getMonth` 方法會傳回介於 0 \(一月\) 和 11 \(十二月\) 之間的整數。  如果是以 "Jan 5, 1996" 建構的 `Date`，`getMonth` 會傳回 0。  
  
## 備註  
 若要利用全球定位時間 \(UTC\) 取得月份值，請使用 `getUTCMonth` 方法。  
  
## 範例  
 下列範例示範如何使用 `getMonth` 方法。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMonth());  
  
// Output: 0  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getUTCMonth 方法 \(日期\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth 方法 \(日期\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCMonth 方法 \(日期\)](../../javascript/reference/setutcmonth-method-date-javascript.md)