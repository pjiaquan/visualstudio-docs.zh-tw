---
title: "@cc_on 陳述式 (JavaScript) | Microsoft Docs"
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
  - "@cc_on_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "@cc_on 陳述式"
  - "@if 陳述式"
  - "@set 陳述式"
  - "條件式編譯, 啟動"
ms.assetid: fdeda7ee-b9f4-4e52-8aa2-21c90c02a332
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# @cc_on 陳述式 (JavaScript)
在指令碼的註解內啟用條件式編譯支援。  
  
> [!WARNING]
>  Internet Explorer 11 標準模式和 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]應用程式不支援條件式編譯。  Internet Explorer 10 標準模式 \(含\) 以前的所有版本都支援條件式編譯。  
  
## 語法  
  
```  
@cc_on   
```  
  
## 備註  
 `@cc_on` 陳述式會啟用指令碼中註解內的條件式編譯。  
  
 通常不會在為 ASP 或 ASP.NET 網頁或命令列程式所撰寫的指令碼中使用條件式編譯變數，因為可以使用其他方法判斷編譯器的功能。  
  
 當您為網頁撰寫指令碼時，一律遠將條件式編譯程式碼放入註解中。  如此可讓不支援條件式編譯的主應用程式將它忽略。  
  
 強烈建議您在註解中使用 `@cc_on` 陳述式，讓不支援條件式編譯的瀏覽器接受您的指令碼做為有效的語法：  
  
 註解外部的 `@if` 或 `@set` 陳述式也會啟用條件式編譯。  
  
## 範例  
 以下範例將示範如何使用 `@cc_on` 陳述式。  
  
```javascript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on the 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on the 16-bit version of Windows.");  
    @else  
        document.write("Running on a different operating system.");  
    @end  
@*/  
```  
  
## 需求  
 所有 Internet Explorer 版本都支援，但是 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]應用程式不支援。  
  
## 請參閱  
 [條件式編譯](../../javascript/advanced/conditional-compilation-javascript.md)   
 [條件式編譯變數](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@if 陳述式](../../javascript/reference/at-if-statement-javascript.md)   
 [@set 陳述式](../../javascript/reference/at-set-statement-javascript.md)