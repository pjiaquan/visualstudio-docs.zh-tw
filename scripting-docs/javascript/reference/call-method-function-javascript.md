---
title: "call 方法 (函式) (JavaScript) | Microsoft Docs"
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
  - "call"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "call 方法"
ms.assetid: fa356dec-48e6-4f75-8bf3-c1814a76818f
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# call 方法 (函式) (JavaScript)
呼叫物件的方法，以其他物件取代目前的物件。  
  
## 語法  
  
```  
call([thisObj[, arg1[, arg2[,  [, argN]]]]])  
```  
  
## 參數  
 `thisObj`  
 選擇項。  為目前的使用物件。  
  
 `arg1, arg2, , argN`  
 選擇項。  要傳遞給方法的引數清單。  
  
## 備註  
 `call` 方法是用來代替另一個物件呼叫方法。  此方法可讓您將函式的 `this` 物件從原始內容變成由 `thisObj` 所指定的新物件。  
  
 如果未提供 `thisObj` 的話，將使用 `global` 物件做為 `thisObj`。  
  
## 範例  
 下列程式碼將示範如何使用 `call` 方法。  
  
```javascript  
function callMe(arg1, arg2){  
    var s = "";  
  
    s += "this value: " + this;  
    s += "<br />";  
    for (i in callMe.arguments) {  
        s += "arguments: " + callMe.arguments[i];  
        s += "<br />";  
    }  
    return s;  
}  
  
document.write("Original function: <br/>");  
document.write(callMe(1, 2));  
document.write("<br/>");  
  
document.write("Function called with call: <br/>");  
document.write(callMe.call(3, 4, 5));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with call:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 請參閱  
 [Function 物件](../../javascript/reference/function-object-javascript.md)   
 [apply 方法 \(函式\)](../../javascript/reference/apply-method-function-javascript.md)