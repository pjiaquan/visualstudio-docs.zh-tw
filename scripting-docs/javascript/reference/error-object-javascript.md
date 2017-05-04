---
title: "Error 物件 (JavaScript) | Microsoft Docs"
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
  - "Error"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Error 物件"
ms.assetid: 0b27d6ec-3997-4e91-a6c0-5afbaf494db7
caps.latest.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 25
---
# Error 物件 (JavaScript)
包含錯誤的相關資訊。  
  
## 語法  
  
```  
  
      errorObj = new Error()  
errorObj = new Error([number])  
errorObj = new Error([number[, description]])  
```  
  
## 參數  
 `errorObj`  
 必要項。  要對其指派 `Error` 物件的變數名稱。  當您使用 `throw` 陳述式建立錯誤時，會省略變數指派。  
  
 `number`  
 選擇項。  指派給錯誤的數值。  如果省略，則為零。  
  
 `description`  
 選擇項。  描述錯誤的簡短字串。  如果省略，則為空字串。  
  
## 備註  
 每當執行階段錯誤發生時，就會建立 `Error` 物件的執行個體來描述錯誤。  這個執行個體具有 `description` 和 `number` 內建屬性，前者包含錯誤描述，後者則包含錯誤代碼。  如需詳細資訊，請參閱 [JavaScript 執行階段錯誤](../../javascript/reference/javascript-run-time-errors.md)。  
  
 錯誤代碼是一個 32 位元的值。  前 16 個位元文字代表設備碼 \(Facility Code\)，後 16 個位元文字才是實際的錯誤代碼。  
  
 您也可以使用上方所示的語法明確建立 `Error` 物件，或使用 `throw` 陳述式擲回該物件。  在這兩種情況下，您都可以加入自己選擇的任何屬性來擴充 `Error` 物件的功能。  
  
 一般而言，在 **try...catch** 陳述式中建立的區域變數都會參考隱含建立的 `Error` 物件。  因此，您可以依自己喜好的方式使用錯誤代碼和描述。  
  
## 範例  
 以下範例將示範 `Error` 物件的用法。  
  
```  
function checkInput(x) {  
    try  
    {  
        if (isNaN(parseInt(x))) {  
            throw new Error("Input is not a number.");  
        }  
    }  
    catch(e)  
    {  
        document.write(e.description);  
    }  
}  
  
checkInput("not a number");  
```  
  
## 範例  
 以下範例將示範隱含建立之 `Error` 物件的用法。  
  
```javascript  
try  
   {  
   // Cause an error.  
   x = y;  
   }  
catch(e)  
   {  
      document.write(e);  
      document.write ("<br />");  
  
      document.write ("Number: ");  
      document.write (e.number & 0xFFFF);  
      document.write ("<br />");  
  
      document.write ("Facility Code: ");  
      document.write(e.number>>16 & 0x1FFF);  
      document.write ("<br />");  
  
      document.write ("Description: ");  
      document.write (e.description);  
   }  
  
// Output:  
// ReferenceError: 'y' is undefined  
// Number: 5009  
// Facility Code: 10  
// Description: 'y' is undefined  
  
```  
  
## 方法  
 [toString 方法 \(錯誤\)](../../javascript/reference/tostring-method-error.md) &#124; [valueOf 方法 \(日期\)](../../javascript/reference/valueof-method-date.md)  
  
## 屬性  
 [constructor 屬性 \(錯誤\)](../../javascript/reference/constructor-property-error.md) &#124; [description 屬性](../../javascript/reference/description-property-error-javascript.md) &#124; [message 屬性](../../javascript/reference/message-property-error-javascript.md) &#124; [name 屬性](../../javascript/reference/name-property-error-javascript.md) &#124; [number 屬性](../../javascript/reference/number-property-error-javascript.md) &#124; [prototype 屬性 \(錯誤\)](../../javascript/reference/prototype-property-error.md) &#124; [stack 屬性 \(錯誤\)](../../javascript/reference/stack-property-error-javascript.md) &#124; [stackTraceLimit 屬性 \(錯誤\)](../../javascript/reference/stacktracelimit-property-error-javascript.md)  
  
## 需求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## 請參閱  
 [new 運算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [throw 陳述式](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally 陳述式](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [var 陳述式](../../javascript/reference/var-statement-javascript.md)   
 [Hilo JavaScript 範例應用程式 \(Windows 市集\)](http://hilojs.codeplex.com/SourceControl/latest)