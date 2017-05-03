---
title: "try...catch...finally 陳述式 (JavaScript) | Microsoft Docs"
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
  - "try_JavaScriptKeyword"
  - "finally_JavaScriptKeyword"
  - "catch_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "try-catch 例外狀況處理"
  - "try-catch 例外狀況處理, 關於 try-catch 例外狀況處理"
  - "try-catch 例外狀況處理, catch 區塊"
  - "try-catch 例外狀況處理, finally 區塊"
ms.assetid: b7a0a54e-dfaa-4e41-bf25-bcaa43e601fb
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# try...catch...finally 陳述式 (JavaScript)
建立程式碼區塊，其中在某一個區塊中擲回的錯誤會在另一個區塊中處理。  `try` 區塊內擲回的錯誤會在 `catch` 區塊中攔截。  [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## 語法  
  
```  
try {  
    tryStatements  
}  
catch(exception){  
    catchStatements  
}  
finally {  
    finallyStatements  
}  
```  
  
## 參數  
 `tryStatements`  
 必要項。  可能發生錯誤的陳述式。  
  
 `exception`  
 必要項。  任何變數名稱。  `exception` 的初始值就是擲回之錯誤的值。  
  
 `catchStatements`  
 選擇項。  用來處理在相關聯 `tryStatements` 中發生之錯誤的陳述式。  
  
 `finallyStatements`  
 選擇項。  在所有其他錯誤處理都發生之後，無條件執行的陳述式。  
  
## 備註  
 對於在特定程式碼區塊中發生的某些或所有錯誤，`try...catch...finally` 陳述式提供了處理方式，同時可繼續執行程式碼。  如果發生未處理的錯誤，則 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 會提供一般錯誤訊息。  
  
 `try` 區塊包含可能引發錯誤的程式碼，而 `catch` 區塊則包含處理部分或所有錯誤的程式碼。  如果 `try` 區塊中發生錯誤，則程式控制權會轉移給 `catch` 區塊。  `exception` 的值就是在 `try` 區塊中發生之錯誤的值。  如果沒有發生錯誤，則 `catch` 區塊中的程式碼永遠不會執行。  
  
 您可以使用 `throw` 陳述式重新擲回錯誤，將錯誤傳遞至更高一個層級。  
  
 在執行過之 `try` 區塊中的所有陳述式，並且已在 `catch` 區塊中完成錯誤處理之後，不管錯誤是否已處理，都會執行 `finally` 區塊中的陳述式。  除非發生未處理的錯誤 \(例如，**catch** 區塊內的執行階段錯誤\)，否則 `finally` 區塊中的程式碼一定會執行。  
  
## 範例  
 下列範例會導致擲回 `ReferenceError` 例外狀況，並顯示錯誤的名稱和錯誤訊息。  
  
```javascript  
try {  
    addalert("bad call");  
}  
catch(e) {  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF);  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
  
// Output:  
Error Message: 'addalert' is undefined  
Error Code: 5009  
Error Name: ReferenceError  
  
```  
  
## 範例  
 下列範例將示範如何重新擲回錯誤以及執行巢狀 `try…catch` 區塊。  如果錯誤是從巢狀 `try` 區塊擲回，就會傳遞至巢狀 `catch` 區塊，而該區塊將重新擲回錯誤。  巢狀 `finally` 區塊會在外部 `catch` 區塊處理錯誤之前，以及在外部 `finally` 區塊執行結束時執行。  
  
```javascript  
try {  
    document.write("Outer try running...<br/>");  
  
    try {  
        document.write("Nested try running...<br/>");  
        throw new Error(301, "an error");  
    }  
    catch (e) {  
        document.write ("Nested catch caught " + e.message + "<br/>");  
        throw e;  
    }  
    finally {  
        document.write ("Nested finally is running...<br/>");  
    }  
}  
catch (e) {  
    document.write ("Outer catch caught " + e.message + "<br/>");  
}  
finally {  
    document.write ("Outer finally running");  
}  
  
// Output:  
// Outer try running...  
// Nested try running...  
// Nested catch caught error from nested try  
// Nested finally is running...  
// Outer catch caught error from nested try  
// Outer finally running  
```  
  
## 需求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
> [!NOTE]
>  從 Internet Explorer 8 標準模式開始，已不再需要 **catch** 區塊來執行 `finally`。  
  
## 請參閱  
 [throw 陳述式](../../javascript/reference/throw-statement-javascript.md)   
 [指令碼愛用者組態精靈範例應用程式](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)