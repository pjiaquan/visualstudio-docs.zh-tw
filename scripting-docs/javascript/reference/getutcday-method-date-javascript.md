---
title: "getUTCDay 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "getUTCDay"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date 物件"
  - "日期，UTC"
  - "UTC 日期，傳回"
  - "getUTCDay 方法"
ms.assetid: 2fceb5b0-6f77-4919-82c3-0877fd55bacb
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# getUTCDay 方法 (日期) (JavaScript)
利用全球定位時間 \(UTC\) 取得當週的日次。  
  
## 語法  
  
```  
  
dateObj.getUTCDay()   
```  
  
#### 參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## 傳回值  
 傳回介於 0 \(星期日\) 和 6 \(星期六\) 之間的整數，表示當週的日次。  
  
## 備註  
 若要利用本地時間取得當週的日次，請使用 `getDate` 方法。  
  
## 範例  
 下列範例示範如何使用 `getUTCDay` 方法。  
  
```javascript  
var date = new Date("2/6/2001");  
var day = date.getUTCDay();  
document.write(day);  
  
// Output: 2  
  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getDay 方法 \(日期\)](../../javascript/reference/getday-method-date-javascript.md)