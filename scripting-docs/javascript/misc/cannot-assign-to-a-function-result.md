---
title: "無法指定給函式結果 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5003"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 無法指定給函式結果
您嘗試指派值給函式結果。  函式結果可以指派給變數，但是不能當成變數使用。  如果您要將新的值指派給函式本身，請省略括號 \(函式呼叫運算子\)。  下列範例會示範產生這個錯誤的情況。  
  
```  
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### 若要更正這個錯誤  
  
-   不要「指派」函式呼叫結果的值。  但是，您可以將函式呼叫的結果指派給「變數」。  
  
    ```javascript  
    myVar = myFunction(42);  
    ```  
  
-   或者，您可以將函式本身 \(而不是它的傳回值\) 指派給變數。  
  
    ```javascript  
    myFunction = new Function("return 42;");  
    ```  
  
## 請參閱  
 [Function 物件](../../javascript/reference/function-object-javascript.md)   
 [撰寫 JavaScript 程式碼](../../javascript/writing-javascript-code.md)   
 [函式](../../javascript/functions-javascript.md)