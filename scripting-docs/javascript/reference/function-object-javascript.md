---
title: "Function 物件 (JavaScript) | Microsoft Docs"
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
  - "function"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Function 物件"
ms.assetid: d3834767-203c-475e-848c-95c423ba15b6
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Function 物件 (JavaScript)
用來建立新的函式。  
  
## 語法  
  
```  
function functionName([argname1  [, ...[, argnameN]]])  
{  
   body  
}  
```  
  
## 語法  
  
```  
  
functionName = new Function( [argname1,  [... argnameN,]] body );  
```  
  
## 參數  
 `functionName`  
 必要項。  新建立的函式名稱  
  
 `argname1...argnameN`  
 選擇項。  函式接受的引數清單。  
  
 `body`  
 選擇項。  包含呼叫函式時所要執行之 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 程式碼區塊的字串。  
  
## 備註  
 此函式是 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中的基本資料型別。  語法 1 會建立函式值，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 會在必要時將此值轉換為 `Function` 物件。  當呼叫函式時，[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 會將語法 2 建立的 `Function` 物件轉換為函式值。  
  
 語法 1 是在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 中建立新函式的標準方法。  語法 2 是用來明確建立函式物件的替代表單。  
  
 例如，若要宣告一個函式並將兩個引數傳遞給它，您可以使用下列兩種方式的其中一種：  
  
## 範例 1  
  
```javascript  
function add(x, y)  
{  
   return(x + y);  
}  
```  
  
## 範例 2  
  
```  
var add = function(x, y) {  
     return(x+y);  
}  
```  
  
 不論是哪種情況，您都可以使用類似以下的程式碼行來呼叫函式：  
  
```javascript  
add(2, 3);  
```  
  
> [!NOTE]
>  當您呼叫函式時，請務必包含括號以及任何必要的引數。  如果呼叫沒有括號的函式則會傳回函式本身，而不是函式的傳回值。  
  
## 屬性  
 [0...  
          n 屬性](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md) &#124;[arguments 屬性](../../javascript/reference/arguments-property-function-javascript.md) &#124; [callee 屬性](../../javascript/reference/callee-property-arguments-javascript.md) &#124; [caller 屬性](../../javascript/reference/caller-property-function-javascript.md) &#124; [constructor 屬性](../../javascript/reference/constructor-property-object-javascript.md) &#124; [length 屬性 \(函式\)](../../javascript/reference/length-property-function-javascript.md) &#124; [prototype 屬性](../../javascript/reference/prototype-property-object-javascript.md)  
  
## 方法  
 [apply 方法](../../javascript/reference/apply-method-function-javascript.md) &#124; [bind 方法](../../javascript/reference/bind-method-function-javascript.md) &#124; [call 方法](../../javascript/reference/call-method-function-javascript.md) &#124; [toString 方法](../../javascript/reference/tostring-method-object-javascript.md) &#124; [valueOf 方法](../../javascript/reference/valueof-method-object-javascript.md)  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## 請參閱  
 [function 陳述式](../../javascript/reference/function-statement-javascript.md)   
 [new 運算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [var 陳述式](../../javascript/reference/var-statement-javascript.md)