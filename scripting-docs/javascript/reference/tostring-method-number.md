---
title: "toString 方法 (數字) | Microsoft Docs"
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
ms.assetid: 07c3484b-d9d8-4451-a2be-88a19a081966
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# toString 方法 (數字)
傳回數字的字串表示。  
  
## 語法  
  
```  
  
number.toString()  
```  
  
## 參數  
 `number`  
 必要項。  要表示為字串的數字。  
  
## 傳回值  
 數字的字串表示。  
  
## 範例  
 以下範例說明如何搭配數字使用 **toString** 方法。  
  
```javascript  
var number = 234.567;  
var s = number.toString();  
document.write(s.length);  
  
// Output: 7  
  
```  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]