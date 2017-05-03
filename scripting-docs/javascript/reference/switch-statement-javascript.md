---
title: "switch 陳述式 (JavaScript) | Microsoft Docs"
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
  - "switch_JavaScriptKeyword"
  - "default_JavaScriptKeyword"
  - "case_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "switch 陳述式"
ms.assetid: 61f80e8b-3739-4146-a893-c2832d92b28c
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# switch 陳述式 (JavaScript)
當指定之運算式的值符合某個標籤時，啟用一個或多個陳述式的執行。  
  
## 語法  
  
```  
switch (expression) {  
    case label :  
        statementlist  
    case label :  
    default :  
        statementlist  
}   
```  
  
## 參數  
 `expression`  
 要評估的運算式。  
  
 `label`  
 要根據 `expression` 比對的識別項。  如果 `label` 為 `expression`，則會立刻開始執行冒號後面的 `statementlist`，直到 `break` 陳述式 \(選擇項\) 出現，或 `switch` 陳述式結束為止。  
  
 `statementlist`  
 要執行的一個或多個陳述式。  
  
## 備註  
 使用 `default` 子句，以提供在沒有標籤值與 `expression` 相符的情況下要執行的陳述式。  它可以出現在 `switch` 程式碼區塊中的任何位置。  
  
 可指定零或多個 `label` 區塊。  如果沒有任何 `label` 與 `expression` 的值相符，而且並未提供 `default` 案例，則不會執行任何陳述式。  
  
 `switch` 陳述式的執行程序如下：  
  
-   評估 `expression` 並依序查看 `label`，直到找到符合的項目為止。  
  
-   如果 `label` 值等於 `expression`，請執行其隨附的 `statementlist`。  
  
     繼續執行，直到 `break` 陳述式出現或 `switch` 陳述式結束為止。  這表示若不使用 `break` 陳述式，就會執行多個 `label` 區塊。  
  
-   如果沒有任何 `label` 等於 `expression`，請移至 `default` 案例。  如果沒有 `default` 案例，則跳到最後一個步驟。  
  
-   繼續執行 `switch` 程式碼區塊結尾後面的陳述式。  
  
## 範例  
 以下的範例會測試物件的型別。  
  
```javascript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
            break;  
        case Number:  
            document.write("Object is a Number.");  
            break;  
        case String:  
            document.write("Object is a String.");  
            break;  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.  
  
// Output when obj is a Number:  
// Object is a Number.  
  
// Output when obj is a String:  
// Object is a String.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## 範例  
 下列程式碼說明當您不使用 `break` 陳述式時會發生什麼事。  
  
```javascript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
        case Number:  
            document.write("Object is a Number.");  
        case String:  
            document.write("Object is a String.");  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a Number:  
// Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a String:  
// Object is a String.Object is unknown.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 請參閱  
 [break 陳述式](../../javascript/reference/break-statement-javascript.md)   
 [if...else 陳述式](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)