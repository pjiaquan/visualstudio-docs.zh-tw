---
title: "Debug 物件 (JavaScript) | Microsoft Docs"
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
  - "debug"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Debug 物件"
  - "偵錯物件, 關於 Debug 物件"
ms.assetid: 42a367ec-beb1-4e59-8342-34c326eca042
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Debug 物件 (JavaScript)
將輸出傳送給偵錯工具的內建全域物件。  
  
## 語法  
  
```  
Debug.function  
```  
  
## 備註  
 您不必讓 Debug 物件執行個體化。 呼叫 `function` 就可以存取其所有屬性和方法。  
  
 還有其他方式可以偵錯 Internet Explorer 和 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式。 在 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式中，`Debug` 物件的 `write` 和 `writeln` 函式會在執行階段於 Visual Studio 的 \[輸出\] 視窗中顯示字串。 如需偵錯 [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] 應用程式的詳細資訊，請參閱[在 Visual Studio 中偵錯應用程式](~/debugger/debug-store-apps-in-visual-studio.md)。  
  
 若要偵錯 Internet Explorer 指令碼，您必須安裝指令碼偵錯工具，且指令碼必須在偵錯模式中執行。 Internet Explorer 8 和更新版本都附有 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 偵錯工具。 如果使用舊版的 Internet Explorer，請參閱[如何：從 Internet Explorer 啟用和啟動指令碼偵錯](http://go.microsoft.com/fwlink/?LinkId=133801)。  
  
 如不偵錯指令碼，函式就不會有任何作用。  
  
## 範例  
 這個範例使用 `write` 函式顯示變數的值。  
  
```javascript  
var counter = 42; Debug.write("The value of counter is " + counter);  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 常數  
 [偵錯常數](../../javascript/reference/debug-constants.md)  
  
## 屬性  
 [Debug.debuggerEnabled 屬性](../../javascript/reference/debug-debuggerenabled-property.md) &#124; [Debug.setNonUserCodeExceptions 屬性](../../javascript/reference/debug-setnonusercodeexceptions-property.md)  
  
## 函式  
 [Debug.msTraceAsyncCallbackStarting 函式](../../javascript/reference/debug-mstraceasynccallbackstarting-function.md) &#124; [Debug.msTraceAsyncCallbackCompleted 函式](../../javascript/reference/debug-mstraceasynccallbackcompleted-function.md) &#124; [Debug.msTraceAsyncOperationCompleted 函式](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md) &#124; [Debug.msTraceAsyncOperationStarting 函式](../../javascript/reference/debug-mstraceasyncoperationstarting-function.md) &#124; [Debug.msUpdateAsyncCallbackRelation 函式](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md) &#124; [Debug.write 函式](../../javascript/reference/debug-write-function-javascript.md) &#124; [Debug.writeln 函式](../../javascript/reference/debug-writeln-function-javascript.md)  
  
## 請參閱  
 [debugger 陳述式](../../javascript/reference/debugger-statement-javascript.md)