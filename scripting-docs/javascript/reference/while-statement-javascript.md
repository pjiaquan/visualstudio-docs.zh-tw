---
title: "while 陳述式 (JavaScript) | Microsoft Docs"
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
  - "while_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "迴圈結構，while 陳述式"
  - "while 陳述式"
ms.assetid: d63777cf-0e1a-4555-8d3a-334381001f48
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# while 陳述式 (JavaScript)
執行陳述式或連串的陳述式，直到指定的條件變成 `false` 為止。  
  
## 語法  
  
```  
while (expression) {  
    statements  
}   
```  
  
## 參數  
 `expression`  
 必要項。  在每次反覆運算迴圈之前所檢查的布林 \(Boolean\) 運算式。  如果 `expression` 是 `true`，則會執行迴圈。  如果 `expression` 是 `false`，則會結束迴圈。  
  
 `statements`  
 選擇項。  要在 `expression` 為 `true` 時執行的一個或多個陳述式。  
  
## 備註  
 `while` 陳述式會在第一次執行迴圈之前先檢查 `expression`。  如果此時 `expression` 是 `false`，表示迴圈從未執行過。  
  
## 範例  
 以下範例說明 `while` 陳述式的用法。  
  
```javascript  
var i = 0;  
var j = 10;  
while (i < 100) {  
    if (i == j)  
        break;  
    i++;  
}  
document.write(i);  
  
// Output: 10  
  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [break 陳述式](../../javascript/reference/break-statement-javascript.md)   
 [continue 陳述式](../../javascript/reference/continue-statement-javascript.md)   
 [do...while 陳述式](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for 陳述式](../../javascript/reference/for-statement-javascript.md)   
 [for...in 陳述式](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)