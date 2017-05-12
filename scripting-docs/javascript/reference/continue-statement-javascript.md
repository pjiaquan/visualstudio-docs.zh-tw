---
title: "continue 陳述式 (JavaScript) | Microsoft Docs"
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
  - "continue_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "continue 陳述式"
  - "do...while 陳述式"
  - "迴圈結構, continue 陳述式"
ms.assetid: f8a30d9f-e2de-4e1f-8668-4e4cf95f7df9
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# continue 陳述式 (JavaScript)
停止目前的迴圈反覆項目，並啟動新的反覆項目。  
  
## 語法  
  
```  
continue [label];  
```  
  
## 備註  
 選擇性 `label` 引數會指定套用 `continue` 的陳述式。  
  
 您只能在 `while`、`do...while`、**for** 或 `for...in` 迴圈中使用 `continue` 陳述式。  執行 `continue` 陳述式會停止目前的迴圈反覆運算，並繼續以迴圈開頭執行程式流程。  這對於不同類型的迴圈會產生下列不同的結果：  
  
-   `while` 和 `do...while` 迴圈會測試它們的條件，如果為 true，就再執行一次迴圈。  
  
-   `for` 迴圈會執行它們的遞增運算式，而如果測試運算式為 true，就再執行一次迴圈。  
  
-   `for...in` 迴圈會繼續執行指定之變數的下一個欄位，並且再執行一次迴圈。  
  
## 範例  
 在此範例中，迴圈會從 1 到 9 反覆執行。  由於使用 `continue` 陳述式搭配 `(i < 5)` 運算式，因此會略過 `continue` 和  `for` 主體結尾之間的陳述式。  
  
```javascript  
for (var i = 1; i < 10; i++) {  
    if (i < 5) {  
        continue;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 5 6 7 8 9  
```  
  
 在下列程式碼中，`continue` 陳述式會參考前面有 `Inner:` 標籤的 `for` 迴圈。  當 `j` 為 24 時，`continue` 陳述式會讓該 `for` 迴圈進入下一個反覆運算。  每一行都會列印 21 到 23 以及 25 到 30 的數字。  
  
```javascript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
             continue Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
//Output:  
//i: 1 j: 21 22 23 25 26 27 28 29 30   
//i: 2 j: 21 22 23 25 26 27 28 29 30   
//i: 3 j: 21 22 23 25 26 27 28 29 30   
//i: 4 j: 21 22 23 25 26 27 28 29 30   
//i: 5 j: 21 22 23 25 26 27 28 29 30   
//i: 6 j: 21 22 23 25 26 27 28 29 30   
//i: 7 j: 21 22 23 25 26 27 28 29 30   
//i: 8 j: 21 22 23 25 26 27 28 29 30   
//i: 9 j: 21 22 23 25 26 27 28 29 30   
//i: 10 j: 21 22 23 25 26 27 28 29 30  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [break 陳述式](../../javascript/reference/break-statement-javascript.md)   
 [do...while 陳述式](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for 陳述式](../../javascript/reference/for-statement-javascript.md)   
 [for...in 陳述式](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [標記陳述式](../../javascript/reference/labeled-statement-javascript.md)   
 [while 陳述式](../../javascript/reference/while-statement-javascript.md)