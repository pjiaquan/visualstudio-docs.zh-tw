---
title: "for 陳述式 (JavaScript) | Microsoft Docs"
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
  - "for_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "迴圈結構, for 陳述式"
ms.assetid: bae0ec40-152e-43f3-969b-3696489ec5c4
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# for 陳述式 (JavaScript)
只要指定的條件為 true，就執行陳述式中的一個區塊。  
  
## 語法  
  
```  
for ([initialization]; [test]; [increment])  
   statement   
```  
  
## 參數  
 `initialization`  
 選擇項。  運算式。  此運算式只會在迴圈執行之前執行一次。  
  
 `test`  
 選擇項。  Boolean 運算式。  如果 `test` 為 `true`，則執行 `statement`。  如果 `test` 是 `false`，便會結束此迴圈。  
  
 `increment`  
 選擇項。  運算式。  遞增運算式會在每次通過迴圈的結尾執行。  
  
 `statement`  
 選擇項。  當 `test` 為 **true** 時所要執行的一個或多個陳述式。  可以是複合陳述式。  
  
## 備註  
 要執行特定次數的迴圈時，您通常可使用 `for` 迴圈。  `for` 迴圈是用來逐一查看陣列以及執行循序處理的有用工具。  
  
 條件運算式的測試是在迴圈執行前進行，所以 `for` 陳述式可能不會執行，也可能執行一次以上。  
  
 您可以在 `for` 迴圈陳述式區塊內的任一行，使用 `break` 陳述式結束此迴圈，或是使用 `continue` 陳述式將控制移轉到迴圈內的下一個反覆運算。  
  
## 範例  
 在下列範例中，`for` 陳述式會執行括號內的陳述式，如下所示：  
  
-   首先，評估變數 `i` 的初始值。  
  
-   接著，只要 `i` 的值小於或等於 9，就會執行 `document.write` 陳述式，並重新評估 `i`。  
  
-   當 `i` 大於 9 時，條件會變成 false 且程式控制權會轉移到迴圈之外。  
  
```javascript  
// i is set to 0 at the start and is incremented by 1 at the  
// end of each iteration.  
// The loop terminates when i is not less than or equal to  
// 9 before a loop iteration.  
for (var i = 0; i <= 9; i++) {  
   document.write (i);  
   document.write (" ");  
}  
  
// Output: 0 1 2 3 4 5 6 7 8 9  
```  
  
## 範例  
 `for` 陳述式的所有運算式都是選擇性。  在下列範例中，`for` 陳述式會建立無限迴圈，而 `break` 陳述式則用來結束該迴圈。  
  
```javascript  
var j = 0;  
for (;;) {  
    if (j >= 5) {  
        break;  
    }  
    j++;  
    document.write (j + " ");  
}  
  
// Output: 1 2 3 4 5  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [for...in 陳述式](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [while 陳述式](../../javascript/reference/while-statement-javascript.md)