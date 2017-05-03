---
title: "getUTCFullYear 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "getUTCFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "getUTCFullYear 方法"
  - "Date 物件"
  - "UTCFullYear 方法"
  - "日期，UTC"
  - "UTC 日期，傳回"
  - "Full Year 方法"
  - "UTC 日期，取得"
ms.assetid: f11e5363-ef8a-48dd-9d56-4ee7290c7c48
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCFullYear 方法 (日期) (JavaScript)
利用全球定位時間 \(UTC\) 取得年份。  
  
## 語法  
  
```  
  
dateObj.getUTCFullYear()   
```  
  
#### 參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## 傳回值  
 傳回以四位數表示的年份。  在 `Date` 建構函式或 `setFullYear` 中以兩位數指定的年份會假設為二十世紀，因此指定 "5\/14\/12"，`getUTCFullYear` 會傳回 "1912"。  
  
## 備註  
 若要利用本地時間取得年份，請使用 `getFullYear` 方法。  
  
## 範例  
 下列範例示範如何使用 `getUTCFullYear` 方法。  
  
```javascript  
var date = new Date("1/9/36");  
document.write(date.getUTCFullYear());  
  
// Output: 1936  
  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getFullYear 方法 \(日期\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [setFullYear 方法 \(日期\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear 方法 \(日期\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)