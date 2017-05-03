---
title: "compile 方法 (規則運算式) (JavaScript) | Microsoft Docs"
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
  - "compile"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Compile 方法"
  - "編譯原始程式碼, 規則運算式"
  - "規則運算式, 編譯"
ms.assetid: dc28cae3-478d-49b5-b5ea-203e5edfe195
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# compile 方法 (規則運算式) (JavaScript)
將規則運算式編譯成內部格式，加快執行速度。  
  
## 語法  
  
```  
  
rgExp.compile(pattern, [flags])   
```  
  
## 參數  
 `rgExp`  
 必要項。  **規則運算式**物件的執行個體。  可以是變數名稱或常值。  
  
 *pattern*  
 必要項。  包含要編譯之規則運算式模式的字串運算式。  
  
 `flags`  
 選擇項。  可組合的可用旗標如下：  
  
-   g \(執行全域搜尋，找出所有符合 *pattern* 的子項目\)  
  
-   i \(不區分大小寫\)  
  
-   m \(多行搜尋\)  
  
## 備註  
 **compile** 方法會將 *pattern* 轉換成內部格式以加快執行速度。  舉例來說，這會讓迴圈中的規則運算式使用起來更有效率。  在不斷重新使用同樣運算式的情況下，編譯過的規則運算式執行速度更快。  不過如果規則運算式有所變更，就失去了運用此方法的好處。  
  
## 範例  
 以下範例說明如何使用 **compile** 方法：  
  
```javascript  
function CompileDemo(){  
   var rs;  
   var s = "AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPp"  
   // Create regular expression for uppercase only.  
   var r = new RegExp("[A-Z]", "g");  
   var a1 = s.match(r)              // Find matches.  
   // Compile the regular expression for lowercase only.  
   r.compile("[a-z]", "g");  
// Find matches.  
   var a2 = s.match(r)                
   return(a1 + "\n" + a2);  
}  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)  
  
## 請參閱  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-tw/ab0766e1-7037-45ed-aa23-706f58358c0e)