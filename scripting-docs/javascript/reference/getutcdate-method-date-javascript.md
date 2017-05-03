---
title: "getUTCDate 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "getUTCDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date 物件"
  - "日期，UTC"
  - "UTC 日期，傳回"
  - "getUTCDate 方法"
ms.assetid: 9e4c763f-c94c-44c9-9684-cb632d75b62e
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# getUTCDate 方法 (日期) (JavaScript)
利用全球定位時間 \(UTC\) 取得月份日期。  
  
## 語法  
  
```  
  
dateObj.getUTCDate()   
```  
  
#### 參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## 傳回值  
 傳回介於 1 和 31 之間的整數，表示月份日期。  
  
## 備註  
 若要使用當地時間取得月份日期，請使用 `getDate` 方法。  
  
## 範例  
 下列範例示範如何使用 `getUTCDate` 方法。  
  
```javascript  
var date = new Date("1/23/2001");  
document.write(date.getUTCDate());  
  
// Output: 23  
  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getDate 方法 \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [setDate 方法 \(Date\)](../../javascript/reference/setdate-method-date-javascript.md)   
 [setUTCDate 方法 \(日期\)](../../javascript/reference/setutcdate-method-date-javascript.md)