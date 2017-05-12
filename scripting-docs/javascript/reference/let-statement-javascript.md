---
title: "let 陳述式 (JavaScript) | Microsoft Docs"
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
  - "let_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "let 陳述式"
  - "宣告變數，let 陳述式"
ms.assetid: c7e4f8a9-8f54-47b6-aed2-956959c1ecfd
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# let 陳述式 (JavaScript)
宣告區塊範圍變數。  
  
## 語法  
  
```  
let variable1 = value1  
```  
  
#### 參數  
 `variable1`  
 正在宣告的變數名稱  
  
 `value1`  
 為變數指定的初始值。  
  
## 備註  
 使用 `let` 陳述式來宣告變數，其範圍限於宣告所在的區塊。  您可以在宣告變數時為變數指派值，或是之後在指令碼中指派。  
  
 使用 `let` 宣告的變數，在其宣告之前無法使用，否則會發生錯誤。  
  
 如果您未初始化 `let` 陳述式中的變數，系統會自動指派 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 值 `undefined` 給此變數。  
  
## 範例  
 以下範例說明 `let` 陳述式的用法。  
  
```javascript  
var  l = 10;  
{  
    let l = 2;  
   // At this point, l = 2.  
}  
// At this point, l = 10.  
  
// Additional ways to declare a variable using let.  
let index;  
let name = "Thomas Jefferson";  
let answer = 42, counter, numpages = 10;  
let myarray = new Array();  
  
```  
  
## 需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 請參閱  
 [const 陳述式](../../javascript/reference/const-statement-javascript.md)   
 [new 運算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array 物件](../../javascript/reference/array-object-javascript.md)   
 [變數](../../javascript/variables-javascript.md)