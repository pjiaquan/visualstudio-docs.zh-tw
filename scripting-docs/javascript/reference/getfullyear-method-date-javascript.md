---
title: "getFullYear 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "getFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日期，傳回年份"
  - "Date 物件"
  - "getFullYear 方法"
ms.assetid: f9ec1262-02e9-4791-90b5-48f33b1dc4bc
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# getFullYear 方法 (日期) (JavaScript)
利用本地時間取得年份。  
  
## 語法  
  
```  
  
dateObj.getFullYear()   
```  
  
#### 參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## 傳回值  
 以四位數表示的年份。  例如，1976 年就會傳回 1976。  在 `Date` 建構函式或 `setFullYear` 中以兩位數指定的年份會假設為二十世紀，因此指定 "5\/14\/12"，`getFullYear` 會傳回 "1912"。  
  
## 備註  
 若要利用全球定位時間 \(UTC\) 取得年份，請使用 `getUTCFullYear` 方法。  
  
## 範例  
 以下範例說明如何使用 **getFullYear** 方法。  
  
```javascript  
var date = new Date("1/1/01");  
document.write(date.getFullYear());  
  
// Output: 1901  
  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getUTCFullYear 方法 \(日期\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear 方法 \(日期\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear 方法 \(日期\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)