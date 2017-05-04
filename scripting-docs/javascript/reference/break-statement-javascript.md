---
title: "break 陳述式 (JavaScript) | Microsoft Docs"
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
  - "break_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "break 陳述式"
  - "do...while 陳述式"
ms.assetid: 5be0f2a8-5fe7-4a6c-89af-ca20a925ce87
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# break 陳述式 (JavaScript)
結束目前迴圈，或與某個 `label` 一起使用時會結束相關的陳述式。  
  
## 語法  
  
```  
break [label];  
```  
  
## 備註  
 `label` 選擇性引數會指定您要中斷之陳述式的標籤。  
  
 您通常可以在 `switch` 陳述式及 `while`、`for`、`for...in` 或 `do...while` 等迴圈中使用 `break` 陳述式。  您通常可在 `switch` 陳述式中使用 `label` 引數，但也可在任何簡單或複合陳述式中使用此引數。  
  
 執行 `break` 陳述式會結束目前迴圈或陳述式，然後利用緊接在後的陳述式開始執行指令碼。  
  
## 範例  
 在此範例中，計數器設定為從 1 數到 99，不過 `break` 陳述式會在數到 14 之後結束迴圈。  
  
```javascript  
for (var i = 1; i < 100; i++) {  
    if (i == 15) {  
        break;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 1234567891011121314  
```  
  
 在下列程式碼中，`break` 陳述式參考到前面有 `Inner:` 陳述式的 `for` 迴圈。  當 `j` 等於 24 時，`break` 陳述式會使程式流程結束該迴圈。  每一行都會列印 21 到 23 的數字。  
  
```javascript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
            break Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
// Output:   
// i: 1 j: 21 22 23   
// i: 2 j: 21 22 23   
// i: 3 j: 21 22 23   
// i: 4 j: 21 22 23   
// i: 5 j: 21 22 23   
// i: 6 j: 21 22 23   
// i: 7 j: 21 22 23   
// i: 8 j: 21 22 23   
// i: 9 j: 21 22 23   
// i: 10 j: 21 22 23  
  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [continue 陳述式](../../javascript/reference/continue-statement-javascript.md)   
 [do...while 陳述式](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for 陳述式](../../javascript/reference/for-statement-javascript.md)   
 [for...in 陳述式](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [標記陳述式](../../javascript/reference/labeled-statement-javascript.md)   
 [while 陳述式](../../javascript/reference/while-statement-javascript.md)