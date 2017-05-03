---
title: "不支援數值引數中的循環參照 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5034"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 不支援數值引數中的循環參照
嘗試叫用了具有無效值的 `JSON.stringify`。  `value` 引數、陣列或物件包含循環參考。  
  
### 若要更正這個錯誤  
  
-   從引數中移除循環參考。  
  
## 範例  
 此範例中的程式碼會產生執行階段錯誤，因為 `john` 具有 `mary` 的參考，而且 `mary` 具有 `john` 的參考。  若要移除循環參考，請移除或取消設定 `mary` 物件的 `brother` 屬性或 `john` 物件的 `sister` 屬性。  
  
```javascript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## 請參閱  
 [JSON 物件](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse 函式](../../javascript/reference/json-parse-function-javascript.md)   
 [JavaScript 執行階段錯誤](../../javascript/reference/javascript-run-time-errors.md)