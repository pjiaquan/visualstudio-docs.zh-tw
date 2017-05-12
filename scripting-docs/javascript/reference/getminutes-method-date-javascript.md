---
title: "getMinutes 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "getMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetMinutes 方法"
  - "minutes 方法"
ms.assetid: d4139b5d-04e1-474c-9a83-e9d40597243a
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getMinutes 方法 (日期) (JavaScript)
會使用本地時間取得 `Date` 物件的分鐘。  
  
## 語法  
  
```  
  
dateObj.getMinutes()   
```  
  
#### 參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## 傳回值  
 會傳回介於 0 和 59 之間的整數。  若時間是在整點小時之後的一分鐘之內，則會傳回零。  如果 `Date` 物件在建立時沒有指定時間，預設的分鐘值為 0。  
  
## 備註  
 若要利用全球定位時間 \(UTC\) 取得分鐘值，請使用 `getUTCMinutes` 方法。  
  
## 範例  
 下列範例示範如何使用 `getMinutes` 方法。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getMinutes());  
  
// Output:  
// 0  
// 5  
  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getUTCMinutes 方法 \(日期\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setMinutes 方法 \(日期\)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes 方法 \(日期\)](../../javascript/reference/setutcminutes-method-date-javascript.md)