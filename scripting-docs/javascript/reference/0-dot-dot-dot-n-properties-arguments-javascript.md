---
title: "0...n 屬性 (引數) (JavaScript) | Microsoft Docs"
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
  - "0...n"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "0...n 屬性"
ms.assetid: 52857c4b-3d56-4500-93ff-4db4729c2578
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 0...n 屬性 (引數) (JavaScript)
傳回 **arguments** 物件中個別引數的實際值，該物件是由執行中函式的 **arguments** 屬性所傳回。  
  
## 語法  
  
```  
[function.]arguments[[0|1|2|...|n]]  
```  
  
## 參數  
 *function*  
 選擇項。  目前正在執行的 `Function` 物件名稱。  
  
 0, 1, 2, *, n*  
 必要項。  介於 0 到 *n* 的非負數整數，其中 0 代表第一個引數，而 *n* 代表最後一個引數。  最後一個引數 *n* 的值是 **arguments.length\-1**。  
  
## 備註  
 0 傳回的值。  .  .  n 個屬性是指傳遞給執行中函式的實際值。  雖然這不是真正的引數陣列，但是組成 **arguments** 物件的個別引數會使用與存取陣列元素相同的方式來存取。  
  
## 範例  
 下列範例說明如何使用 **0 . . .**  ***n*** 屬性 \(這些是 **arguments** 物件的屬性\)。  如果要完全了解這個範例，將傳遞一個或多個引數給函式：  
  
```javascript  
function ArgTest(){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello", new Date()));  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用於**：[arguments 物件](../../javascript/reference/arguments-object-javascript.md)&#124; [Function 物件](../../javascript/reference/function-object-javascript.md)  
  
## 請參閱  
 [length 屬性 \(引數\)](../../javascript/reference/length-property-arguments-javascript.md)   
 [length 屬性 \(函式\)](../../javascript/reference/length-property-function-javascript.md)