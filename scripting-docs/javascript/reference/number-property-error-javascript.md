---
title: "number 屬性 (錯誤) (JavaScript) | Microsoft Docs"
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
  - "Number"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Number 屬性"
ms.assetid: 8697e20b-a2b0-4e26-85c0-ab07ddfe8281
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# number 屬性 (錯誤) (JavaScript)
傳回或設定與特定錯誤相關的數值。  `Error` 物件的預設屬性是 **number**。  
  
## 語法  
  
```  
  
object  
.number [= errorNumber]  
```  
  
## 參數  
 *Object*  
 `Error` 物件的任何執行個體。  
  
 *errorNumber*  
 表示錯誤的整數。  
  
## 備註  
 錯誤號碼是一個 32 位元的值。  前 16 個位元代表設備代碼，後 16 個位元才是錯誤碼。  若要找出錯誤碼，請使用 `&` \(位元 And\) 運算子，以結合 number 屬性與十六進位數字 `0xFFFF`。  
  
## 範例  
 下列範例會導致例外狀況的擲回，並顯示從錯誤代碼所衍生的錯誤碼。  
  
```javascript  
try  
    {  
    // Cause an error.  
    var x = y;  
    }  
catch(e)  
    {  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
  
    document.write ("Facility Code: ")  
    document.write(e.number>>16 & 0x1FFF)  
    document.write ("<br />");  
  
    document.write ("Error Message: ")  
    document.write (e.message)  
    }  
```  
  
## 範例  
 這個程式碼的輸出如下。  
  
```javascript  
Error Code: 5009  
Facility Code: 10  
Error Message: 'y' is undefined  
```  
  
## 需求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **適用於**：[Error 物件](../../javascript/reference/error-object-javascript.md)  
  
## 請參閱  
 [description 屬性 \(錯誤\)](../../javascript/reference/description-property-error-javascript.md)   
 [message 屬性 \(錯誤\)](../../javascript/reference/message-property-error-javascript.md)   
 [name 屬性 \(錯誤\)](../../javascript/reference/name-property-error-javascript.md)