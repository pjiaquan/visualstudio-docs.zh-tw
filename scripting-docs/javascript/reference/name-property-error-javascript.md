---
title: "name 屬性 (錯誤) (JavaScript) | Microsoft Docs"
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
  - "name"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Name 屬性"
  - "name 屬性, 錯誤名稱"
ms.assetid: 94df2d6b-f1a1-4931-a956-0a930cb87f76
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# name 屬性 (錯誤) (JavaScript)
傳回錯誤的名稱。  
  
## 語法  
  
```  
  
errorObj.  
name  
  
```  
  
## 參數  
 `errorObj`  
 必要項。  `Error` 物件的執行個體。  
  
## 備註  
 **name** 屬性會傳回錯誤的名稱或例外狀況類型。  發生執行階段錯誤時，name 屬性會設成下列其中一個原生例外狀況類型：  
  
|例外狀況類型|意義|  
|------------|--------|  
|ConversionError|每當嘗試將物件轉換成無法轉換的型別時，就會發生這個錯誤。|  
|RangeError|提供給函式的引數超出允許的範圍時，就會發生這個錯誤。  例如，建構 `Array` 物件時，若嘗試使用不是有效的正整數長度，就會發生這個錯誤。|  
|ReferenceError|當偵測到無效參考時，就會發生這個錯誤。  例如，如果預期的參考是 `null`，就會發生這個錯誤。|  
|RegExpError|規則運算式發生編譯錯誤時，就會發生這個錯誤。  然而，規則運算式一旦經過編譯後，就不可能發生這個錯誤。  例如，如果宣告規則運算式所用的模式語法無效，或旗標不是 **i**、**g** 或 **m**，或同一個旗標出現不止一次，就會發生這樣的例子。|  
|SyntaxError|當剖析原始程式文字，而該原始程式文字不符合正確語法時，就會發生這個錯誤。  例如，如果呼叫 `eval` 函式時所用的引數不是有效的程式文字，就會發生這樣的錯誤。|  
|TypeError|只要運算元實際的型別不符合預期型別時，就會發生這個錯誤。  例如，如果對非物件的項目呼叫函式，或這個項目不支援該呼叫，就會發生這樣的例子。|  
|URIError|偵測到不合法的 Uniform Resource Indicator \(URI\) 時發生錯誤。  例如，在編碼或解碼的字串中發現非法的字元時，就會發生這個錯誤。|  
  
## 範例  
 下列範例會導致擲回 TypeError 例外狀況，並顯示錯誤的名稱和錯誤訊息。  
  
```javascript  
try  
{  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## 範例  
 這個程式碼的輸出如下。  
  
```javascript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用於**：[Error 物件](../../javascript/reference/error-object-javascript.md)  
  
## 請參閱  
 [description 屬性 \(錯誤\)](../../javascript/reference/description-property-error-javascript.md)   
 [message 屬性 \(錯誤\)](../../javascript/reference/message-property-error-javascript.md)   
 [number 屬性 \(錯誤\)](../../javascript/reference/number-property-error-javascript.md)