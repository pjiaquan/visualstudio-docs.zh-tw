---
title: "valueOf 方法 (日期) | Microsoft Docs"
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
ms.assetid: 39a1f96e-14b0-4db2-b53d-cdfd67cbb208
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# valueOf 方法 (日期)
傳回從 UTC 1970 年 1 月 1 日午夜起算，儲存在物件中的時間值 \(以毫秒為單位\)  
  
## 語法  
  
```  
  
date.valueOf()  
```  
  
#### 參數  
 `date` 物件是 Date 的任何執行個體。  
  
## 傳回值  
 從 UTC 1970 年 1 月 1 日午夜起算，儲存在物件中的時間值 \(以毫秒為單位\)  這個值與 `getTime` 的傳回值相同。  
  
## 範例  
 下列範例說明如何搭配日期使用 `valueOf` 方法。  
  
```javascript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
if (myDate.getTime() == myDate.valueOf())  
    document.write("values are the same");  
else  
    document.write("values are different");  
  
// Output: values are the same  
  
```  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]