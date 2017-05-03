---
title: "test 方法 (規則運算式) (JavaScript) | Microsoft Docs"
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
  - "test"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "測試方法"
ms.assetid: 4f4b6e39-cb1a-4be9-a66f-7b846075580d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# test 方法 (規則運算式) (JavaScript)
傳回的布林值將說明所搜尋的字串中是否有模式存在。  
  
## 語法  
  
```  
  
rgExp.test(str)   
```  
  
## 參數  
 `rgExp`  
 必要項。  包含規則運算式模式和適用旗標之**規則運算式**物件的執行個體。  
  
 `str`  
 必要項。  用來執行搜尋的字串。  
  
## 備註  
 **test** 方法會檢查字串中是否有模式存在，若有則傳回 **true**，否則傳回 **false**。  
  
 **test** 方法不會修改全域 `RegExp` 物件的屬性。  
  
## 範例  
 以下範例說明如何使用 **test** 方法。  若要使用以下範例，請將規則運算式模式及字串提供給函式。  此函式會測試字串中是否出現該規則運算式模式，然後傳回表示搜尋結果的字串：  
  
```javascript  
function TestDemo(re, teststring)  
{  
   // Test string for existence of regular expression.  
   var found = re.test(teststring)  
  
   // Format the output.  
   var s = "";  
   s += "'" + teststring + "'"  
  
   if (found)  
      s += " contains ";  
   else  
      s += " does not contain ";  
  
   s += "'" + re.source + "'"  
   return(s);  
}  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)  
  
## 請參閱  
 [RegExp 物件](../../javascript/reference/regexp-object-javascript.md)   
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-tw/ab0766e1-7037-45ed-aa23-706f58358c0e)