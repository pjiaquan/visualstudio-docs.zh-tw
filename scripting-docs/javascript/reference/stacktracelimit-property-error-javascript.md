---
title: "stackTraceLimit 屬性 (錯誤) (JavaScript) | Microsoft Docs"
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
  - "Error.stackTraceLimit"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "錯誤堆疊追蹤限制 [JavaScript]"
  - "JavaScript 錯誤堆疊"
  - "錯誤堆疊 [JavaScript]"
  - "JavaScript 堆疊追蹤限制"
ms.assetid: 127ef8e8-892e-4263-9ebc-03364af01212
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# stackTraceLimit 屬性 (錯誤) (JavaScript)
取得或設定堆疊追蹤限制，這個限制等於要顯示的錯誤框架數目。  預設限制是 10。  
  
## 語法  
  
```  
  
Error  
.stackTraceLimit   
```  
  
## 備註  
 您可以將 `stackTraceLimit` 屬性設定為介於 0 與 `Infinity` 之間的正值。  如果 `stackTraceLimit` 屬性是在擲回錯誤時設定為 0，就不會顯示任何堆疊追蹤。  如果此屬性設定為負值或非數值的值，則值會轉換為 0。  如果 stackTraceLimit 設定為 `Infinity`，則會顯示整個堆疊。  否則會使用 `ToUint32` 轉換該值。  
  
## 範例  
 下列範例示範如何設定堆疊追蹤限制，然後再取得該限制。  
  
```javascript  
try  
    {  
    var err = new Error("my error");  
    Error.stackTraceLimit = 7;  
    throw err;  
    }  
catch(e)  
    {  
    document.write ("Error stack trace limit: ")  
    document.write (Error.stackTraceLimit);  
    }  
```  
  
## 需求  
 Internet Explorer 10 和 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式都支援。  
  
 **適用於**：[Error 物件](../../javascript/reference/error-object-javascript.md)  
  
## 請參閱  
 [description 屬性 \(錯誤\)](../../javascript/reference/description-property-error-javascript.md)   
 [message 屬性 \(錯誤\)](../../javascript/reference/message-property-error-javascript.md)   
 [name 屬性 \(錯誤\)](../../javascript/reference/name-property-error-javascript.md)   
 [stack 屬性 \(錯誤\)](../../javascript/reference/stack-property-error-javascript.md)