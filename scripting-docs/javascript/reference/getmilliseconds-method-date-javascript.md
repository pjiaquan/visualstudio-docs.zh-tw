---
title: "getMilliseconds 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "getMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "毫秒"
  - "getMilliseconds 方法"
ms.assetid: 1b512146-1e8a-44a4-89da-6cc5338d15cb
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getMilliseconds 方法 (日期) (JavaScript)
會使用本地時間取得日期的毫秒。  
  
## 語法  
  
```  
  
dateObj.getMilliseconds()   
```  
  
#### 參數  
 必要的 `dateObj` 參考是 `Date` 物件。  
  
## 傳回值  
 傳回日期的毫秒。  此值的範圍可從 0 到 999。  如果建構日期時沒有指定毫秒，則傳回值為 0。  
  
## 備註  
 若要取得協調世界時 \(Coordinated Universal Time，UTC\) 的毫秒數，請使用 `getUTCMilliseconds` 方法。  
  
## 範例  
 下列範例示範如何使用 **getMilliseconds** 方法。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(5);  
document.write(date.getMilliseconds());  
// Output:   
// 0  
// 5  
  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getUTCMilliseconds 方法 \(日期\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setMilliseconds 方法 \(日期\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds 方法 \(日期\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)