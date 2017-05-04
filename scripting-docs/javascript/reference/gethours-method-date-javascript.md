---
title: "getHours 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "getHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date 物件"
  - "GetHours 方法"
  - "Hours 方法"
ms.assetid: c3936496-a213-4d15-b308-d53926ed310c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getHours 方法 (日期) (JavaScript)
會使用本地時間取得一天中的小時。  
  
## 語法  
  
```  
  
dateObj.getHours()   
```  
  
#### 參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## 傳回值  
 介於 0 到 23 之間的整數，代表從午夜開始的小時數。  如果時間是在 1:00:00 am 之前，會傳回零。  如果 `Date` 物件在建立時沒有指定時間，預設的小時為 0。  
  
## 備註  
 若要利用全球定位時間 \(UTC\) 取得小時值，請使用 `getUTCHours` 方法。  
  
## 範例  
 下列範例示範如何使用 `getHours` 方法。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getHours());  
document.write("<br/>");  
  
date.setTime(50000000);  
document.write(date.getHours());  
  
// Output:  
// 0   
// 5  
  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getUTCHours 方法 \(日期\)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setHours 方法 \(日期\)](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours 方法 \(日期\)](../../javascript/reference/setutchours-method-date-javascript.md)