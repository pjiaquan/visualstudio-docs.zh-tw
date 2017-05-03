---
title: "do...while 陳述式 (JavaScript) | Microsoft Docs"
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
  - "do_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "do...while 陳述式"
  - "終止迴圈"
  - "迴圈結構，do 和 do-while"
ms.assetid: 8b7782ba-fbad-48cd-9639-193566da6ae5
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# do...while 陳述式 (JavaScript)
執行一次陳述式區塊，然後重複執行迴圈，直到條件式運算式評估為 `false` 為止。  
  
## 語法  
  
```  
do {  
    statement  
}  
while (expression) ;   
```  
  
## 參數  
 `statement`  
 必要項。  當 `expression` 為 `true` 時要執行的陳述式。  可以是複合陳述式。  
  
 `expression`  
 必要項。  可以強制轉型為布林值 `true` 或 `false` 的運算式。  如果 `expression` 是 `true`，則會再次執行迴圈。  如果 `expression` 是 `false`，則會結束迴圈。  
  
## 備註  
 `do...while` 迴圈與 `while` 運算式不同，前著會在評估條件運算式之前執行一次。  
  
 您可以在 `do…while` 區塊中的任一行，使用 `break` 陳述式讓程式流程結束此迴圈，或是使用 `continue` 陳述式直接移到 `while` 運算式。  
  
## 範例  
 在下列範例中，只要變數 `i` 小於 10，`do...while` 迴圈中的陳述式就會繼續執行。  
  
```javascript  
var i = 0;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 0 1 2 3 4 5 6 7 8 9   
```  
  
## 範例  
 在下列範例中，即使條件不符合，迴圈中的陳述式都會執行一次。  
  
```javascript  
var i = 10;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 10  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 請參閱  
 [break 陳述式](../../javascript/reference/break-statement-javascript.md)   
 [continue 陳述式](../../javascript/reference/continue-statement-javascript.md)   
 [for 陳述式](../../javascript/reference/for-statement-javascript.md)   
 [for...in 陳述式](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [while 陳述式](../../javascript/reference/while-statement-javascript.md)   
 [標記陳述式](../../javascript/reference/labeled-statement-javascript.md)