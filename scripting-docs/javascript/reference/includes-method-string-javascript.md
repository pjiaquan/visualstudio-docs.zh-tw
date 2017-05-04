---
title: "includes 方法 (字串) (JavaScript) | Microsoft Docs"
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
ms.assetid: 2639e4e5-23ba-424a-80ea-be067a4cd65e
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# includes 方法 (字串) (JavaScript)
傳回布林值，指出字串物件中是否包含傳入的字串。  
  
## 語法  
  
```  
stringObj.includes(substring [, position]);  
```  
  
#### 參數  
 `stringObj`  
 必要項。  要測試的字串物件。  
  
 `substring`  
 必要項。  要測試的字串。  
  
 `position`  
 選擇項。  字串物件中要測試的第一個字元位置，以 0 開頭。  
  
## 傳回值  
 如果字串物件中包含傳入的字串，`includes` 方法就會傳回 `true`；否則會傳回 `false`。  
  
## 備註  
  
## 範例  
  
```javascript  
// Returns true   
"abcde".includes("cd")  
"abcde".includes("cd", 2)  
  
// Returns false  
"abcde".includes("CD")  
"abcde".includes("cd", 3)  
  
```  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]