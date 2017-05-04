---
title: "eval 函式 (JavaScript) | Microsoft Docs"
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
  - "eval"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "eval 函式"
  - "剖析，程式碼"
  - "剖析器"
ms.assetid: 85587e39-9325-4b75-b9f9-9d7d475a2120
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# eval 函式 (JavaScript)
評估並執行 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 程式碼。  
  
## 語法  
  
```  
eval(codeString)   
```  
  
## 參數  
 `codeString`  
 必要項。  包含有效 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 程式碼的 `String` 值。  
  
## 備註  
 `eval` 函式會啟用 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 原始程式碼的動態執行。  
  
 `codeString` 字串會由 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 剖析器剖析並加以執行。  
  
 傳遞至 `eval` 函式的程式碼會在呼叫 `eval` 函式的同時，於同一內容中執行。  
  
 可能的話，請使用 [JSON.parse 函式](../../javascript/reference/json-parse-function-javascript.md)，還原序列化 JavaScript 物件標記法 \(JSON\) 文字。  `JSON.parse` 函式比 `eval` 函式更為安全且執行速度更快。  
  
## 範例  
 下列程式碼會初始化 `myDate` 變數來測試日期。  
  
```javascript  
var dateFn = "Date(1971,3,8)";  
var myDate;  
eval("myDate = new " + dateFn + ";");  
  
document.write(myDate);  
  
// Output: Thu Apr 8 00:00:00 PDT 1971  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[Global 物件](../../javascript/reference/global-object-javascript.md)  
  
## 請參閱  
 [String 物件](../../javascript/reference/string-object-javascript.md)