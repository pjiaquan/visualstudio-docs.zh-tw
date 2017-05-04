---
title: "apply 方法 (函式) (JavaScript) | Microsoft Docs"
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
  - "apply"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Apply 方法"
ms.assetid: b36df78e-b14b-46ca-b5cb-de752d80f40a
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# apply 方法 (函式) (JavaScript)
會呼叫函式，以指定的物件代替函式的 `this` 值，並以指定陣列代替函式的引數。  
  
## 語法  
  
```  
apply([thisObj[,argArray]])  
```  
  
## 參數  
 `thisObj`  
 選擇項。  用來做為 `this` 物件的物件。  
  
 `argArray`  
 選擇項。  要傳遞給此函式的一組引數。  
  
## 備註  
 如果 `argArray` 不是有效的物件，則會發生「必須要有物件」錯誤。  
  
 如果 `argArray` 和 `thisObj` 兩者都未提供的話，將使用原來的 `this` 物件做為 `thisObj`，而且不傳送任何引數。  
  
## 範例  
 下列程式碼將示範如何使用 apply 方法。  
  
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
  
document.write("Function called with apply: <br/>");  
document.write(callMe.apply(3, [ 4, 5 ]));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with apply:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 請參閱  
 [Function 物件](../../javascript/reference/function-object-javascript.md)