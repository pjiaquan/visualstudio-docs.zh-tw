---
title: "endsWith 方法 (字串) (JavaScript) | Microsoft Docs"
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
ms.assetid: c7d836e3-bc43-4d1b-be60-0a93beb8b7a2
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# endsWith 方法 (字串) (JavaScript)
傳回值，指出字串或子字串的結尾是否為另一個指定的字串。  
  
## 語法  
  
```vb  
  
stringObj.endsWith(str, [, position]);  
```  
  
#### 參數  
 `stringObj`  
 必要項。  要搜尋的字串物件。  
  
 `str`  
 必要項。  搜尋字串。  
  
 `position`  
 選擇項。  字串物件中要搜尋的第一個字元位置，從 0 開始。  
  
## 傳回值  
 如果開頭為 `position` 的字串位於搜尋字串的結尾，則 `endsWith` 方法會傳回 `true`；否則傳回 `false`。  
  
## 例外狀況  
 如果 `str` 是 `RegExp`，則會擲回 `TypeError`。  
  
## 備註  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]