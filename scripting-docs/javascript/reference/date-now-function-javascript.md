---
title: "Date.now 函式 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "now 方法"
ms.assetid: 41beda89-1a40-4fb1-88b0-38c090af739b
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Date.now 函式 (JavaScript)
取得目前的日期和時間。  
  
## 語法  
  
```  
  
Date.now()  
```  
  
## 傳回值  
 從 1970 年 1 月 1 日午夜起直到現在日期及時間的毫秒數。  
  
## 備註  
 [getTime 方法](../../javascript/reference/gettime-method-date-javascript.md)會傳回從 1970 年 1 月 1 日起直到指定之日期的毫秒數。  
  
 如需如何計算已經過的時間以及比較日期的詳細資訊，請參閱[計算日期和時間 \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)。  
  
## 範例  
 在下列程式碼中，說明了如何使用 `now` 方法。  
  
```javascript  
var start = Date.now();  
var response = prompt("What is your name?", "");  
var end = Date.now();  
var elapsed = (end - start) / 1000;  
document.write("You took " + elapsed + " seconds" + " to type: " + response);  
  
// Output:  
// You took <seconds> seconds to type: <name>  
```  
  
## 需求  
 Internet Explorer 9 之前的版本不支援。  不過，下列文件模式會提供支援：Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準、Internet Explorer 10 標準。  也在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式中受到支援。  
  
## 請參閱  
 [getTime 方法 \(日期\)](../../javascript/reference/gettime-method-date-javascript.md)   
 [Date 物件](../../javascript/reference/date-object-javascript.md)   
 [計算日期和時間 \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)   
 [JavaScript 方法](../../javascript/reference/javascript-methods.md)