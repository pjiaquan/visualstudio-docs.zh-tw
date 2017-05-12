---
title: "caller 屬性 (函式) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "caller"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "caller 屬性"
  - "函式呼叫，正在執行的函式"
ms.assetid: ae210853-7160-4102-9cfd-ab489f180ce1
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# caller 屬性 (函式) (JavaScript)
取得叫用目前函式的函式。  
  
## 語法  
  
```  
  
functionName.caller  
```  
  
## 備註  
 `functionName` 物件是任何執行中函式的名稱。  
  
 `caller` 屬性只會定義給正在執行的函式。  如果從 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 程式的頂層呼叫函式，則 `caller` 會包含 `null`。  
  
 如果 `caller` 屬性使用於字串內容中，則其結果與 `functionName`.`toString` 相同，也就是說，會顯示出函式的解譯文字。  
  
 下列範例說明 `caller` 屬性的使用方式：  
  
```javascript  
function CallLevel(){  
   if (CallLevel.caller == null)  
      return("CallLevel was called from the top level.");  
   else  
      return("CallLevel was called by another function.");  
}  
  
document.write(CallLevel());  
  
// Output: CallLevel was called from the top level.  
```  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## 請參閱  
 [function 陳述式](../../javascript/reference/function-statement-javascript.md)