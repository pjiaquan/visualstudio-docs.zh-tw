---
title: "toString 方法 (錯誤) | Microsoft Docs"
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
ms.assetid: 5d6d9712-c06d-4b31-9bc9-e46f6bb5cd38
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# toString 方法 (錯誤)
傳回表示錯誤的字串。  
  
## 語法  
  
```  
  
error.toString()  
```  
  
## 參數  
 `date`  
 必要項。  要表示為字串的錯誤。  
  
## 傳回值  
 傳回「錯誤:」加上錯誤訊息。  
  
## 範例  
 下列範例說明如何搭配錯誤使用 `toString` 方法。  
  
```javascript  
var myError = new Error();  
myError.message = "My Error";  
var errorString = myError.toString();  
document.write(errorString);  
  
// Output: Error: My Error  
  
```  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]