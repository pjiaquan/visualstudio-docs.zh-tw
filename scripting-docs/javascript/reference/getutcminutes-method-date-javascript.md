---
title: "getUTCMinutes 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "getUTCMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "分鐘"
  - "UTC 時間，傳回"
  - "getUTCMinutes 方法"
ms.assetid: b6d92543-b285-4e46-8f47-bba36e53fabd
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCMinutes 方法 (日期) (JavaScript)
使用全球定位時間 \(UTC\)，取得 `Date` 物件的資料錄。  
  
## 語法  
  
```  
  
dateObj.getUTCMinutes()   
```  
  
#### 參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## 傳回值  
 傳回介於 0 和 59 之間的整數。  零小於一分鐘傳回時間在整點小時之後。  如果 `Date` 建立物件，但沒有指定時間，根據預設 UTC 分鐘值設定為 0。  然而，在其他時區它可能就會不同。  
  
## 備註  
 若要利用本地時間取得所儲存的分鐘數，請使用 `getMinutes` 方法。  
  
## 範例  
 在下列程式碼中，說明了如何使用 `getUTCMinutes` 方法。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getUTCMinutes());  
  
// Output:   
// 0  
// 5  
  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getMinutes 方法 \(日期\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [setMinutes 方法 \(日期\)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes 方法 \(日期\)](../../javascript/reference/setutcminutes-method-date-javascript.md)