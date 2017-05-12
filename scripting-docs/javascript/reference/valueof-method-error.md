---
title: "valueOf 方法 (錯誤) | Microsoft Docs"
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
ms.assetid: ca25c57d-c9ad-445b-8235-561390de680c
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# valueOf 方法 (錯誤)
傳回錯誤的字串值。  
  
## 語法  
  
```  
  
error.valueOf()  
```  
  
#### 參數  
 `error` 物件是 Error 的任何執行個體。  
  
## 傳回值  
 「錯誤:」這個字串加上錯誤訊息。  
  
## 範例  
 下列範例說明如何搭配日期使用 `valueOF` 方法。  
  
```javascript  
var myError = new Error();  
myError.message = "This is an error.";  
var value = myError.valueOf();  
document.write(value);  
  
// Output: Error: This is an error.  
  
```  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]