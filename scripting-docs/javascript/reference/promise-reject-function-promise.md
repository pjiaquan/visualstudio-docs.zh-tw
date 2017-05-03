---
title: "Promise.reject 函式 (承諾) | Microsoft Docs"
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
ms.assetid: 9746e15b-9717-4e36-bf6b-910dcc6cd667
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Promise.reject 函式 (承諾)
建立包含等同於傳入引數之結果的新被拒承諾。  
  
## 語法  
  
```  
Promise.reject(r);  
```  
  
#### 參數  
 `r`  
 必要項。  承諾被拒的原因。  
  
## 備註  
 處理當被拒承諾傳回時，執行 `then` 或 `catch` 方法之函數時所發生的錯誤。  
  
## 範例  
  
```javascript  
var p = Promise.reject('failure');  
p.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
```  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## 請參閱  
 [Promise 物件](../../javascript/reference/promise-object-javascript.md)