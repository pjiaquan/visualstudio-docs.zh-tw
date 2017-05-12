---
title: "codePointAt 方法 (字串) (JavaScript) | Microsoft Docs"
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
ms.assetid: 7979018f-1be3-4a13-9e8f-c84c7ed35288
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# codePointAt 方法 (字串) (JavaScript)
傳回 Unicode UTF\-16 字元的字碼指標。  
  
## 語法  
  
```  
stringObj.codePointAt(pos);  
```  
  
#### 參數  
 `stringObj`  
 必要項。  字串物件。  
  
 `pos`  
 必要項。  字元的位置。  
  
## 備註  
 這個方法會傳回所有 UTF\-16 字元的字碼指標值，包括星號字碼指標 \(具有四個以上十六進位值的字碼指標\)。  
  
 如果 `pos` 小於零 \(0\) 或大於字串的大小，則傳回值為 `undefined`。  
  
## 範例  
 下列範例會示範如何使用 `codePointAt` 方法。  
  
```javascript  
var cp1 = "𠮷".codePointAt(0);  
vary cp2 = 'abc'.codePointAt(1);  
  
if(console && console.log) {  
    console.log(cp1);  
    console.log(cp2);}  
  
// Output:  
// 0x20BB7  
// 98  
  
```  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]