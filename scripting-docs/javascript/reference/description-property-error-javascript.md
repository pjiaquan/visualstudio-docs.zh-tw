---
title: "description 屬性 (錯誤) (JavaScript) | Microsoft Docs"
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
  - "Description"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Description 屬性"
  - "錯誤處理, 錯誤描述"
  - "錯誤, description"
ms.assetid: ea727f1e-2041-4400-965c-67e6d47a1ff0
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# description 屬性 (錯誤) (JavaScript)
傳回或設定與特定錯誤相關的描述字串。  
  
## 語法  
  
```  
  
object  
.description [= stringExpression]  
```  
  
## 參數  
 *object*  
 必要項。  `Error` 物件的任何執行個體。  
  
 `stringExpression`  
 選擇項。  包含錯誤描述的字串運算式。  
  
## 備註  
 **description** 屬性會包含與特定錯誤相關的錯誤訊息字串。  使用這個屬性中包含的值，向使用者提出錯誤的警示。  
  
 **description** 和 **message** 屬性提供相同的功能。**description** 屬性提供回溯相容性，而 **message** 屬性則符合 ECMA 標準。  
  
## 範例  
 以下範例示範 **description** 屬性的用法。  
  
```javascript  
try  
{  
// Cause an error:  
    x = y     
}  
catch(e)  
{  
// Prints "[object Error]":  
    document.write(e)  
    document.write (" ");  
// Prints 5009:  
    document.write((e.number & 0xFFFF))    
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.description);  
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.message)  
}  
```  
  
## 需求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **適用於**：[Error 物件](../../javascript/reference/error-object-javascript.md)  
  
## 請參閱  
 [number 屬性 \(錯誤\)](../../javascript/reference/number-property-error-javascript.md)   
 [message 屬性 \(錯誤\)](../../javascript/reference/message-property-error-javascript.md)   
 [name 屬性 \(錯誤\)](../../javascript/reference/name-property-error-javascript.md)