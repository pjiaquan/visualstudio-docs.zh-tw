---
title: "getTime 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "getTime"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetTime 方法"
  - "time 方法"
ms.assetid: f0da1d4e-337c-497d-9205-093defbc6d3d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# getTime 方法 (日期) (JavaScript)
取得時間值 \(以毫秒為單位\)。  
  
## 語法  
  
```  
  
dateObj.getTime()   
```  
  
#### 參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## 傳回值  
 傳回從 1970 年 1 月 1 日午夜到 `Date` 物件中時間值之間的毫秒數。  日期範圍大約是從 1970 年 1 月 1 日午夜前後各約 285,616 年。  負數表示 1970 年以前的日期。  
  
## 備註  
 在計算多個日期和時間時，您可能想將變數定義成等於日、時或分鐘的毫秒數。  例如：  
  
```javascript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
```  
  
 如需如何使用 `getTime` 方法的詳細資訊，請參閱[計算日期和時間 \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)。  
  
## 範例  
 下列範例示範如何使用 `getTime` 方法。  
  
```javascript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
  
date = new Date("1/1/2001");  
var time = date.getTime();  
  
document.write(Math.round(time / day) + " days from 1/1/1970 to 1/1/2001");  
  
// Output: 11323 days from 1/1/1970 to 1/1/2001  
  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [setTime 方法 \(日期\)](../../javascript/reference/settime-method-date-javascript.md)