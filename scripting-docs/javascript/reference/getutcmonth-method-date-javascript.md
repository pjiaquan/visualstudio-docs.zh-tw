---
title: "getUTCMonth 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "getUTCMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日期，UTC"
  - "UTC 日期，傳回"
  - "Month 方法"
  - "getUTCMonth 方法"
ms.assetid: eabae139-4da0-4e4a-a4cb-608e6375fc9e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCMonth 方法 (日期) (JavaScript)
使用全球定位時間 \(UTC\)，取得 `Date` 物件中的月份。  
  
## 語法  
  
```  
  
dateObj.getUTCMonth()   
```  
  
#### 參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## 傳回值  
 傳回介於 0 \(一月\) 和 11 之間的整數 \(十二月\)。  
  
## 備註  
 若要取得本地時間的月份，請使用 **getMonth** 方法。  
  
## 範例  
 下列範例示範如何使用 `getUTCMonth` 方法。  
  
```javascript  
var date = new Date("2/2/2002");  
document.write(date.getUTCMonth());  
  
// Output: 1  
  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getMonth 方法 \(日期\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [setMonth 方法 \(日期\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCMonth 方法 \(日期\)](../../javascript/reference/setutcmonth-method-date-javascript.md)