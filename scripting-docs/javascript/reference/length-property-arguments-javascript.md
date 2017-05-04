---
title: "length 屬性 (arguments) (JavaScript) | Microsoft Docs"
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
  - "length Property"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Length 屬性"
  - "length 屬性 (arguments)"
ms.assetid: 3cf36823-15bc-489b-a951-24c4923d9dba
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# length 屬性 (arguments) (JavaScript)
傳回由呼叫端傳給函式的實際引數個數。  
  
## 語法  
  
```  
[function.]arguments.length  
```  
  
## 備註  
 選擇性的 *function* 引數是目前正在執行的 `Function` 物件。  
  
 指令碼引擎會在開始執行 `Function` 物件的函式內容時，將傳給此物件的實際引數個數設定為 **arguments** 物件之 **length** 屬性的初始值。  
  
## 範例  
 以下範例示範 **arguments** 物件的 **length** 屬性用法。  雖然範例中的函式需要 2 個引數，但若要完全理解這個範例，請傳遞更多引數給函式：  
  
```javascript  
function ArgTest(a, b){  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
  
   document.write (s);  
}  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用於**：[arguments 物件](../../javascript/reference/arguments-object-javascript.md)&#124; [Function 物件](../../javascript/reference/function-object-javascript.md)  
  
## 請參閱  
 [arguments 屬性 \(函式\)](../../javascript/reference/arguments-property-function-javascript.md)   
 [length 屬性 \(陣列\)](../../javascript/reference/length-property-array-javascript.md)   
 [length 屬性 \(字串\)](../../javascript/reference/length-property-string-javascript.md)