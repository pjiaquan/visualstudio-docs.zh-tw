---
title: "debugger 陳述式 (JavaScript) | Microsoft Docs"
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
  - "debugger_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "debugger 陳述式"
ms.assetid: c6d2e193-c1f7-4fb3-8a4e-cc9823174ae4
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# debugger 陳述式 (JavaScript)
暫停執行。  
  
## 語法  
  
```  
debugger  
```  
  
## 備註  
 您可將 `debugger` 陳述式放在程序中的任何位置來暫停執行。  使用 `debugger` 陳述式類似於在程式碼中設定中斷點。  
  
 `debugger` 陳述式會暫停執行，但是不會關閉任何檔案或清除任何變數。  
  
> [!NOTE]
>  除非正在偵錯指令碼，否則 `debugger` 陳述式不會有任何作用。  
  
## 範例  
 這個範例使用 `debugger` 陳述式，暫停執行每一次的 `for` 迴圈反覆作業。  
  
> [!NOTE]
>  若要執行此範例，您必須已安裝指令碼偵錯工具，而且指令碼必須以偵錯模式執行。  
>   
>  Internet Explorer 8 包含 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 偵錯工具。  如果您是使用舊版 Internet Explorer，請參閱 [HOW TO：從 Internet Explorer 啟用和啟動指令碼偵錯](http://go.microsoft.com/fwlink/?LinkId=133801)。  
  
```javascript  
for(i = 1; i<5; i++) {  
   // Print i to the Output window.  
   Debug.write("loop index is " + i);  
   // Wait for user to resume.  
   debugger  
}  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 請參閱  
 [JavaScript 陳述式](../../javascript/reference/javascript-statements.md)   
 [條件式編譯](../../javascript/advanced/conditional-compilation-javascript.md)