---
title: "Promise.resolve 函式 (承諾) | Microsoft Docs"
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
ms.assetid: 0fb6bff9-54ab-41be-97d7-04f7e6fe9cff
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Promise.resolve 函式 (承諾)
建立新的已解析承諾，其結果等同於其引數。  
  
## 語法  
  
```  
Promise.resolve(x)  
```  
  
#### 參數  
 `x`  
 必要項。  隨已完成的承諾傳回的值。  
  
## 備註  
 傳回已完成的 Promise 物件時，即會執行`then` 方法的履行處理函式。  
  
## 範例  
  
```javascript  
var p = Promise.resolve('success');  
p.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
```  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## 請參閱  
 [Promise 物件](../../javascript/reference/promise-object-javascript.md)