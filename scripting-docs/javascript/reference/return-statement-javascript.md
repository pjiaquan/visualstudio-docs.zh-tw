---
title: "return 陳述式 (JavaScript) | Microsoft Docs"
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
  - "return_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "function 陳述式"
  - "return 陳述式"
  - "return 陳述式, 結束指令碼的函式"
  - "return 陳述式, 語法"
  - "終止執行"
ms.assetid: a9130d90-11fb-43f5-a819-7e5435f74c05
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# return 陳述式 (JavaScript)
結束目前的函式，並從該函式傳回值。  
  
## 語法  
  
```  
  
return[(][expression][)];   
```  
  
## 備註  
 選擇性 *expression* 引數是從此函式傳回的值。  如果省略，函式將不會傳回值。  
  
 您可以使用 `return` 陳述式停止執行函式並傳回 *expression* 的值。  如果省略 *expression*，或未執行函式中的 `return` 陳述式，則會將未定義的值指派給呼叫目前函式的運算式。  
  
## 範例  
 以下範例說明 `return` 陳述式的用法。  
  
```javascript  
function myfunction(arg1, arg2){  
   var r;  
   r = arg1 * arg2;  
   return(r);  
}  
```  
  
## 範例  
 下列範例說明如何使用 `return` 陳述式傳回函式。  
  
```javascript  
function doWork() {  
    return function calculate(y) { return y + 1; };  
}  
  
var func = doWork();  
var x = func(5);  
document.write(x);  
  
// Output: 6  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [function 陳述式](../../javascript/reference/function-statement-javascript.md)