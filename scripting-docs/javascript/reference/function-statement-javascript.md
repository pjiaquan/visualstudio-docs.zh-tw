---
title: "function 陳述式 (JavaScript) | Microsoft Docs"
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
  - "function_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "宣告函式"
  - "宣告函式, 語法"
  - "function 陳述式"
  - "new 運算子"
ms.assetid: cc9cfd43-1305-41c8-ad67-545d20f4fafe
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# function 陳述式 (JavaScript)
宣告新函式。  
  
## 語法  
  
```  
function functionname ([arg1 [, arg2 [,...[, argN]]]]) {  
    statements  
}   
```  
  
## 參數  
 `functionname`  
 必要項。  函式的名稱。  
  
 `arg1...argN`  
 選擇項。  此函式所了解的選擇性引數清單 \(以逗號分隔\)。  
  
 `statements`  
 選擇項。  一個或多個 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 陳述式。  
  
## 備註  
 使用 `function` 陳述式可宣告函式供稍後使用。  `statements` 中包含的程式碼會等到從指令碼中的其他位置呼叫函式之後才執行。  
  
 [return](../../javascript/reference/return-statement-javascript.md) 陳述式是用來傳回函式的值。  您不須使用 `return` 陳述式，當程式到達函式結尾時即會傳回。  如果此函式中未執行任何 `return` 陳述式，或者 `return` 陳述式沒有運算式，此函式會傳回 `undefined` 值。  
  
> [!NOTE]
>  當您呼叫函式時，請務必包含括號以及任何必要的引數。  呼叫沒有括號的函式會傳回此函式的參考，而不是此函式的結果。  
  
## 範例  
 以下範例說明 `function` 陳述式的用法。  
  
```javascript  
function myfunction (arg1, arg2) {  
    var r = arg1 * arg2;  
    return(r);  
}  
```  
  
## 範例  
 函式可指派給變數。  下列範例將說明這種處理方式。  
  
```javascript  
function AddFive(x) {  
    return x + 5;  
}  
  
function AddTen(x) {  
    return x + 10;  
}  
  
var condition = false;  
  
var MyFunc;  
if (condition) {  
    MyFunc = AddFive;  
}  
else {  
    MyFunc = AddTen;  
}  
  
var result = MyFunc(123);  
// Output: 133  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [new 運算子](../../javascript/reference/new-operator-decrementjavascript.md)