---
title: "getUTCHours 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "getUTCHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "小時"
  - "UTC 時間，傳回"
  - "getUTCHours 方法"
ms.assetid: 7c9825dd-4b3a-4614-8e09-f40df123b630
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCHours 方法 (日期) (JavaScript)
使用全球定位時間 \(UTC\)，取得 `Date` 物件中的小時值。  
  
## 語法  
  
```  
  
dateObj.getUTCHours()   
```  
  
#### 參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## 傳回值  
 傳回表示時數 0 和 23 之間的整數表示從午夜。  如果時間是在 1:00 之前，會傳回零: 00 AM。  如果 `Date` 建立物件，但沒有指定時間，根據預設小時 0 為 UTC 時間。  這個可能是非零的其他時區。  
  
## 備註  
 若要利用本地時間取得午夜之後所經過的小時數，請使用 `getHours` 方法。  
  
## 範例  
 在下列程式碼中，說明了如何使用 `getUTCHours` 方法。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCHours());  
document.write("<br/>");  
  
var date2 = new Date("1/1/2001 11:22:33");  
document.write(datee.getUTCHours());  
  
// Output (in the PST time zone):  
// 8  
// 19  
  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getHours 方法 \(日期\)](../../javascript/reference/gethours-method-date-javascript.md)   
 [setHours 方法 \(日期\)](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours 方法 \(日期\)](../../javascript/reference/setutchours-method-date-javascript.md)