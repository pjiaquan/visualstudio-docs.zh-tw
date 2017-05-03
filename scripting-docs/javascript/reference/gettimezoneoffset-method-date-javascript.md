---
title: "getTimezoneOffset 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "getTimeZoneOffset"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "getTimezoneOffset 方法"
  - "時區 [Visual Studio]"
ms.assetid: 58ee22b0-4688-45bd-a337-cc23119b09ce
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# getTimezoneOffset 方法 (日期) (JavaScript)
取得本機電腦時間與全球定位時間 \(UTC\) 之間的分鐘差。  
  
## 語法  
  
```  
  
dateObj.getTimezoneOffset()   
```  
  
#### 參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## 傳回值  
 傳回目前電腦 \(用戶端電腦，或者如果這個方法是從伺服器指令碼呼叫，則為伺服器電腦\) 時間與 UTC 時間之間差異的分鐘數。  如果目前電腦的本地時間是在 UTC 之後 \(如太平洋日光節約時間\)，它是正數，如果目前電腦的本地時間是在 UTC 之前 \(如日本\)，它是負數。  如果洛杉磯的用戶端在 12 月 1 日連絡位於紐約的某部伺服器，在用戶端上執行時，`getTimezoneOffset` 會傳回 480，若在伺服器上執行，則會傳回 300。  
  
## 備註  
  
## 範例  
 下列範例示範如何使用 `getTimezoneOffset` 方法。  
  
```javascript  
var date =  new Date();  
var minutes = date.getTimezoneOffset();  
  
if (minutes < 0)  
    document.write(minutes / 60 + " hours after UTC");  
else  
    document.write(minutes / 60 + " hours before UTC");  
  
// Output (for example, where local time is PST):   
7 hours before UTC  
  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getTime 方法 \(日期\)](../../javascript/reference/gettime-method-date-javascript.md)