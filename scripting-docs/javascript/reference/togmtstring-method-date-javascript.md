---
title: "toGMTString 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "toGMTString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toGMTString 方法"
ms.assetid: 9dc1e722-5722-4b8c-a213-a2650f55f207
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toGMTString 方法 (日期) (JavaScript)
傳回使用格林威治標準時間 \(GMT\) 轉換為字串的日期。  
  
## 語法  
  
```  
  
dateObj.toGMTString()   
```  
  
## 備註  
 必要的 `dateObj` 參考是任何 `Date` 物件。  
  
 `toGMTString` 方法已不再使用，提供的目的只是為了回溯相容性。  建議您改用 `toUTCString` 方法。  
  
 `toGMTString` 方法傳回的 `String` 物件將包含使用 GMT 規格設定格式的日期。  傳回值的格式如下：「1996 年 1 月 5 日 00:00:00 \(GMT\)」。  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[Date 物件](../../javascript/reference/date-object-javascript.md)  
  
## 請參閱  
 [toUTCString 方法 \(日期\)](../../javascript/reference/toutcstring-method-date-javascript.md)