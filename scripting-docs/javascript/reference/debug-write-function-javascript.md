---
title: "Debug.write 函式 (JavaScript) | Microsoft Docs"
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
  - "Write"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "write 方法 [JavaScript]"
ms.assetid: fd1cfbb3-46cb-47cc-896c-a70d457dd413
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# Debug.write 函式 (JavaScript)
將字串傳送至指令碼偵錯工具。  
  
## 語法  
  
```  
  
Debug.write([str1 [, str2 [, ... [, strN]]]])  
```  
  
## 參數  
 *str1, str2, ... , strN*  
 選擇項。  要傳送至指令碼偵錯工具的字串。  
  
## 備註  
 `Debug.write` 函式會在執行階段將字串傳送至指令碼偵錯工具的 \[即時運算\] 視窗。  如果未針對指令碼進行偵錯，`Debug.write` 函式不會有任何作用。  
  
 `Debug.write` 函式幾乎與 `Debug.writeln` 函式完全相同。  唯一的差異在於 `Debug.writeln` 函式會在傳送字串之後傳送新行字元。  
  
## 範例  
 這個範例會在指令碼偵錯工具的 \[即時運算\] 視窗中，使用 `Debug.write` 函式顯示變數的值。  
  
> [!NOTE]
>  若要執行此範例，您必須已安裝指令碼偵錯工具，而且指令碼必須以偵錯模式執行。  
>   
>  Internet Explorer 8 包含 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 偵錯工具。  如果您是使用舊版 Internet Explorer，請參閱 [HOW TO：從 Internet Explorer 啟用和啟動指令碼偵錯](http://go.microsoft.com/fwlink/?LinkId=133801)。  
  
```javascript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[Debug 物件](../../javascript/reference/debug-object-javascript.md)  
  
## 請參閱  
 [Debug.writeln 函式](../../javascript/reference/debug-writeln-function-javascript.md)