---
title: "Debug.writeln 函式 (JavaScript) | Microsoft Docs"
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
  - "writeln"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "writeIn 方法"
ms.assetid: c3aad0cd-0486-4161-9ba6-31d672da72af
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Debug.writeln 函式 (JavaScript)
將字串傳送至指令碼偵錯工具，後面緊接著新行字元。  
  
## 語法  
  
```  
  
Debug.writeln([str1 [, str2 [, ... [, strN]]]])  
```  
  
## 參數  
 *str1, str2, ... , strN*  
 選擇項。  要傳送至指令碼偵錯工具的字串。  
  
## 備註  
 `Debug.writeln` 函式會在執行階段期間，將緊接著新行字元的字串傳送至 Microsoft 指令碼偵錯工具的 \[即時運算\] 視窗。  如果未針對指令碼進行偵錯，`Debug.writeln` 函式不會有任何作用。  
  
 `Debug.writeln` 函式幾乎與 `Debug.write` 函式完全相同。  唯一差異在於 `Debug.write` 函式在傳送字串之後不會傳送新行字元。  
  
## 範例  
 這個範例會使用 `Debug.writeln` 函式，以便在 Microsoft 指令碼偵錯工具的 \[即時運算\] 視窗中顯示變數的值。  
  
> [!NOTE]
>  若要執行此範例，您必須已安裝指令碼偵錯工具，而且指令碼必須以偵錯模式執行。  
>   
>  Internet Explorer 8 包含 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 偵錯工具。  如果您是使用舊版 Internet Explorer，請參閱 [HOW TO：從 Internet Explorer 啟用和啟動指令碼偵錯](http://go.microsoft.com/fwlink/?LinkId=133801)。  
  
```javascript  
var counter = 42;  
Debug.writeln("The value of counter is " + counter);  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[Debug 物件](../../javascript/reference/debug-object-javascript.md)  
  
## 請參閱  
 [Debug.write 函式](../../javascript/reference/debug-write-function-javascript.md)