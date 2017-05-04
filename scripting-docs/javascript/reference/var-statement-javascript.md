---
title: "var 陳述式 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "var_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "宣告變數，var 陳述式"
  - "var 陳述式"
ms.assetid: 56f900af-a5c4-4667-9664-5956d30f0aae
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# var 陳述式 (JavaScript)
宣告變數。  
  
## 語法  
  
```  
var variable1 = value1  
```  
  
## 參數  
 `variable1`  
 正在宣告的變數名稱  
  
 `value1`  
 為變數指定的初始值。  
  
## 備註  
 使用 `var` 陳述式來宣告變數。  您可以在宣告變數時為變數指派值，或是之後在指令碼中指派。  
  
 變數是在第一次出現於指令碼時宣告的。  
  
 您可以宣告變數而不使用 `var` 關鍵字，並為變數指派值。  這稱為「隱含宣告」，但不建議您使用。  隱含宣告會提供全域範圍給變數。  但如果您在程序層級宣告變數，通常您不會希望變數具有全域範圍。  若要避免提供全域範圍給變數，您必須在變數宣告中使用 `var` 關鍵字。  
  
 如果您未初始化 `var` 陳述式中的變數，系統會自動指派 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 值 `undefined` 給此變數。  
  
## 範例  
 下列範例說明 `var` 陳述式的用法。  
  
```javascript  
var index;  
var name = "Thomas Jefferson";  
var answer = 42, counter, numpages = 10;  
var myarray = new Array();  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [function 陳述式](../../javascript/reference/function-statement-javascript.md)   
 [new 運算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array 物件](../../javascript/reference/array-object-javascript.md)   
 [變數](../../javascript/variables-javascript.md)