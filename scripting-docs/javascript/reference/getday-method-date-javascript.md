---
title: "getDay 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "getDay"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetDay 方法"
  - "Date 物件"
  - "日期，傳回星期幾"
ms.assetid: 27be7168-3dce-41c9-ae69-6280b7984c2e
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# getDay 方法 (日期) (JavaScript)
利用本地時間取得當週的日次。  
  
## 語法  
  
```  
  
dateObj. getDay()   
```  
  
#### 參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## 傳回值  
 介於 0 和 6 之間的整數，表示當週的日次 \(星期日是 0，星期六是 6\)。  
  
## 備註  
 若要利用「協調世界時」\(Coordinated Universal Time，UTC\) 取得星期的日期值，請使用 `getUTCDay` 方法。  
  
 下列範例示範如何使用 `getDay` 方法。  
  
```javascript  
var date = new Date("Saturday, February 9, 2008");  
day = date.getDay();  
document.write(day);  
  
// Output: 6  
  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getUTCDay 方法 \(日期\)](../../javascript/reference/getutcday-method-date-javascript.md)