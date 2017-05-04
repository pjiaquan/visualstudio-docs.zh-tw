---
title: "substr 方法 (字串) (JavaScript) | Microsoft Docs"
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
  - "substr"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "substr 方法"
ms.assetid: f12541c1-2623-482e-941d-2e22bc3c4a4a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# substr 方法 (字串) (JavaScript)
取得從指定位置起始且具有指定長度的子字串。  
  
## 語法  
  
```  
  
stringvar.substr(start [, length ])   
```  
  
## 參數  
 `stringvar`  
 必要項。  要從中擷取子字串的字串常值或 `String` 物件。  
  
 `start`  
 必要項。  所需之子字串的起始位置。  字串中第一個字元的索引是零。  
  
 `length`  
 選擇項。  要包含在傳回之子字串中的字元數。  
  
## 備註  
 如果 `length` 是零或負值，則會傳回空字串。  若未指定，則子字串會一直持續到 `stringvar` 的結尾。  
  
## 範例  
 在下列範例中，說明了如何使用 `substr` 方法。  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substr(10, 5);    
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10);  
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10, -5);  
document.write("[" + ss + "] <br>");  
  
// Output:  
// [brown]   
// [brown fox jumps over the lazy dog.]   
// []  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[String 物件](../../javascript/reference/string-object-javascript.md)  
  
## 請參閱  
 [substring 方法 \(字串\)](../../javascript/reference/substring-method-string-javascript.md)