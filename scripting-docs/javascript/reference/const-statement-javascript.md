---
title: "const 陳述式 (JavaScript) | Microsoft Docs"
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
  - "const_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "宣告變數，const 陳述式"
  - "const 陳述式"
ms.assetid: 3ad0840f-437f-4163-9571-86ecc5ddb987
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# const 陳述式 (JavaScript)
宣告具有常數值的區塊範圍變數。  
  
## 語法  
  
```  
const constant1 = value1  
```  
  
#### 參數  
 `constant1`  
 正在宣告的變數名稱  
  
 `value1`  
 為變數指定的初始值。  
  
## 備註  
 使用 `const` 陳述式來宣告常數值的變數，其範圍限於宣告所在的區塊。  無法變更此變數的值。  
  
 使用 `const` 宣告的變數，必須在進行宣告時加以初始化。  
  
## 範例  
 以下範例說明 `const` 陳述式的用法。  
  
```javascript  
var c = 10;  
{  
    const c = 2;  
   // At this point, c = 2.  
}  
// At this point, c = 10.  
  
// Additional ways to declare a variable using const.  
const name = "Thomas Jefferson";  
const answer = 42, numpages = 10;  
const myarray = new Array();  
  
```  
  
## 需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 請參閱  
 [let 陳述式](../../javascript/reference/let-statement-javascript.md)   
 [new 運算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array 物件](../../javascript/reference/array-object-javascript.md)   
 [變數](../../javascript/variables-javascript.md)