---
title: "repeat 方法 (字串) (JavaScript) | Microsoft Docs"
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
ms.assetid: fe02cdfd-f0f6-45a2-ad36-31c4300ef142
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# repeat 方法 (字串) (JavaScript)
傳回新的字串物件，其值等於原始字串重複指定的次數。  
  
## 語法  
  
```  
stringObj.repeat(count);  
```  
  
#### 參數  
 `stringObj`  
 必要項。  字串物件。  
  
 `count`  
 必要項。  要在傳回的字串中重複原始字串的次數。  
  
## 例外狀況  
 這個方法唯有在引數為負數或 \+Infinity 時才會擲回 RangeError。  
  
## 備註  
 `repeat` 方法會將原始字串串連到新字串，並且多達 `count` 所指定的次數。  
  
 如果 `count` 不是小於 `Infinity` 的正數，這個方法會擲回錯誤。  
  
## 範例  
  
```javascript  
"abc".repeat(3); // Returns "abcabcabc"  
"abc".repeat(0); // Returns an empty string.  
```  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]