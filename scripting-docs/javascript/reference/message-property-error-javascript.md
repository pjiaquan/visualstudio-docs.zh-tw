---
title: "message 屬性 (錯誤) (JavaScript) | Microsoft Docs"
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
  - "message"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Message 屬性"
ms.assetid: 8cab0392-e0db-4714-827c-47ab04e8b4f2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# message 屬性 (錯誤) (JavaScript)
傳回錯誤訊息的字串。  
  
## 語法  
  
```  
  
errorObj.message  
```  
  
## 參數  
 `errorObj`  
 必要項。  `Error` 物件的執行個體。  
  
## 備註  
 `message` 屬性會傳回字串，其中包含與特定錯誤相關的錯誤訊息。  
  
 `description` 和 `message` 屬性會提供相同的功能。  `description` 屬性會提供回溯相容性，`message` 屬性則符合 ECMA 標準。  
  
## 範例  
 下列範例會導致擲回 TypeError 例外狀況，並顯示錯誤的名稱和錯誤訊息。  
  
```javascript  
try  
{  
    // Cause an error.  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## 範例  
 這個程式碼的輸出如下。  
  
```javascript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## 需求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **適用於**：[Error 物件](../../javascript/reference/error-object-javascript.md)  
  
## 請參閱  
 [description 屬性 \(錯誤\)](../../javascript/reference/description-property-error-javascript.md)   
 [name 屬性 \(錯誤\)](../../javascript/reference/name-property-error-javascript.md)