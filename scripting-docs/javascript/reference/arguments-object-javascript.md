---
title: "arguments 物件 (JavaScript) | Microsoft Docs"
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
  - "arguments"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "arguments 物件"
  - "引數, arguments 物件"
ms.assetid: 5eb79ca9-bbb8-4a42-aaf5-16a93ecb425f
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# arguments 物件 (JavaScript)
物件，表示目前執行之函式的引數和呼叫該函式的函式。  
  
## 語法  
  
```  
[function.]arguments[n]  
```  
  
## 參數  
 *Function \- 功用*  
 選擇項。  目前正在執行的 `Function` 物件名稱。  
  
 *n*  
 必要項。  傳給 `Function` 物件之引數值的索引 \(以零為起始\)。  
  
## 備註  
 您不可以明確建立 **arguments** 物件。  只有當函式開始執行時，才可使用 **arguments** 物件。  此函式的 **arguments** 物件不是陣列，但個別引數是使用與存取陣列元素相同的方式來存取。  *n* 索引實際上是 **arguments** 物件之其中一個 **0** ***n*** 屬性的參考。  
  
## 範例  
 以下範例說明 **arguments** 物件的用法。  
  
```javascript  
function ArgTest(a, b)  
{  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
   s += "<br />";  
  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++)  
   {  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
  
   document.write(s);  
}  
  
ArgTest(1, 2, "hello", new Date())  
  
// Output:  
// Expected Arguments: 2  
// Passed Arguments: 4  
// The individual arguments are: 1 2 hello Tues Jan 8 08:27:09 PST 20xx  
  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 請參閱  
 [0...n 屬性 \(引數\)](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)   
 [callee 屬性 \(引數\)](../../javascript/reference/callee-property-arguments-javascript.md)   
 [length 屬性 \(引數\)](../../javascript/reference/length-property-arguments-javascript.md)