---
title: "toString 方法 (布林值) | Microsoft Docs"
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
ms.assetid: c46b43c0-6946-407a-b0e0-49cba90e226a
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# toString 方法 (布林值)
傳回物件的字串表示。  
  
## 語法  
  
```  
  
boolean.toString()  
```  
  
## 參數  
 `boolean`  
 必要項。  要取得其字串表示法的物件。  
  
## 傳回值  
 如果布林值為 `true`，則會傳回 "true"，  否則會傳回 "false"。  
  
## 備註  
  
## 範例  
 以下範例說明如何使用 **toString** 方法。  
  
```javascript  
var s = new Boolean(0);  
document.write(s.toString());  
  
// Output: false;  
  
```  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]