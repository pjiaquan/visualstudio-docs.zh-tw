---
title: "arguments 屬性 (函式) (JavaScript) | Microsoft Docs"
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
  - "arguments，arguments 屬性"
  - "Arguments 屬性"
ms.assetid: efc7a1ee-0880-4f05-b0f2-808f31a4af1d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# arguments 屬性 (函式) (JavaScript)
取得目前正在執行之 `Function` 物件的引數。  
  
## 語法  
  
```  
  
function.arguments  
```  
  
## 備註  
 `function` 引數是目前正在執行的函式名稱，而且可以省略。  
  
 此屬性可讓函式處理變動數量的引數。  `arguments` 物件的 **length** 屬性包含傳遞給函式的引數個數。  包含在 `arguments` 物件中的個別引數都可以透過與存取陣列元素相同的方式進行存取。  
  
## 範例  
 下列範例說明 `arguments` 屬性的使用方式：  
  
```javascript  
function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
//Output: function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
// Output: The individual arguments are: 1 2 hello  
```  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## 請參閱  
 [arguments 物件](../../javascript/reference/arguments-object-javascript.md)   
 [function 陳述式](../../javascript/reference/function-statement-javascript.md)