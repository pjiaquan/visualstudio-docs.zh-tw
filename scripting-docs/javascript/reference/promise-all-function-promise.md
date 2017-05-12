---
title: "Promise.all 函式 (承諾) | Microsoft Docs"
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
ms.assetid: 02a7b90c-96f6-4484-9466-d261efa1b494
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Promise.all 函式 (承諾)
聯結兩個以上的承諾，而且只有在完成或拒絕所有指定的承諾時才會傳回。  
  
## 語法  
  
```  
Promise.all(func1, func2 [,funcN])  
```  
  
#### 參數  
 `func1`  
 必要項。  傳回承諾的函式。  
  
 `func2`  
 必要項。  傳回承諾的函式。  
  
 `funcN`  
 選擇項。  傳回承諾的一或多個函式。  
  
## 備註  
 傳回的結果是一個值陣列，這些值是由完成的承諾所傳回。  如果其中一個聯結承諾遭到拒絕，`Promise.all` 立即和遭拒承諾原因一起傳回 \(所有其他傳回值都會被捨棄\)。  
  
## 範例  
 在這段程式碼中，第一個逾時呼叫會在 5000 毫秒後傳回。  只有兩個逾時呼叫都完成或拒絕時，完成處理常式才會呼叫 `Promise.all`。  
  
```javascript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## 請參閱  
 [Promise 物件](../../javascript/reference/promise-object-javascript.md)