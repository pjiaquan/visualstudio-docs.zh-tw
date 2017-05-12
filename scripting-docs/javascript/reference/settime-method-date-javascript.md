---
title: "setTime 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "setTime"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "SetTime 方法"
  - "time 方法"
ms.assetid: 86584748-7219-495b-bf56-e27f5782778c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# setTime 方法 (日期) (JavaScript)
設定 `Date` 物件中的日期及時間值。  
  
## 語法  
  
```  
  
dateObj.setTime(milliseconds)   
```  
  
## 參數  
 `dateObj`  
 必要項。  任何 `Date` 物件。  
  
 *milliseconds*  
 必要項。  表示從 1970 年 1 月 1 日午夜 12 點 \(GMT\) 開始到現在所經過之毫秒數的數值。  
  
## 備註  
 如果 *milliseconds* 是負值，表示日期是在 1970 年之前。  可用日期的範圍大約涵蓋 1970 年前後各約 285,616 年。  
  
 使用 `setTime` 方法設定日期和時間將不受時區影響。  
  
## 範例  
 在下列範例中，說明了如何使用 `setTime` 方法。  
  
```javascript  
function SetTimeTest(newtime){  
   var d, s;                  //Declare variables.  
   d = new Date();            //Create Date object.  
   d.setTime(newtime);        //Set time.  
   s = "Current setting is ";  
   s += d.toUTCString();  
   return(s);                 //Return new setting.  
}  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [getTime 方法 \(日期\)](../../javascript/reference/gettime-method-date-javascript.md)