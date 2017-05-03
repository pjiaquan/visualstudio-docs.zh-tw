---
title: "toString 方法 (日期) | Microsoft Docs"
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
ms.assetid: d3037289-d805-409b-8781-045c59a2c404
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# toString 方法 (日期)
傳回日期的字串表示。  字串格式取決於地區設定。  如果是美國英文 \(en\-us\)，其格式如下：  
  
 *星期* *月份* *日期* *小時*:*分鐘*:*秒* *時區* *年份*  
  
## 語法  
  
```  
  
date.toString()  
```  
  
## 參數  
 `date`  
 必要項。  要表示為字串的日期。  
  
## 傳回值  
 傳回日期的字串表示。  
  
## 範例  
 下列範例說明如何搭配日期使用 `toString` 方法。  
  
```javascript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
var dateString = myDate.toString();  
document.write(dateString);  
  
// Output: <date>  
  
```  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]