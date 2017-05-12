---
title: "exec 方法 (規則運算式) (JavaScript) | Microsoft Docs"
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
  - "exec"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Exec 方法"
  - "比對字串"
ms.assetid: 83092452-60cc-4218-b4ae-af9e3cb96c34
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# exec 方法 (規則運算式) (JavaScript)
利用規則運算式模式執行字串搜尋，然後傳回包含該搜尋結果的陣列。  
  
## 語法  
  
```  
  
rgExp.exec(str)   
```  
  
## 參數  
 `rgExp`  
 必要項。  包含規則運算式模式和適用旗標之**規則運算式**物件的執行個體。  
  
 `str`  
 必要項。  要執行搜尋的目標 `String` 物件或字串常值。  
  
## 備註  
 如果 `exec` 方法找不到符合的項目，便會傳回 `null`。  如果找到符合的項目，則 `exec` 會傳回一個陣列，然後更新全域 `RegExp` 物件的屬性來反映符合項目的結果。  陣列的元素零包含所有相符項目，而元素 1 – *n* 則包含了相符項目中的任何子相符項目。  此行為相當於不設定全域旗標 \(**g**\) 的 `match` 方法。  
  
 如果規則運算式已經設定了全域旗標，`exec` 將會從 `lastIndex` 值指定的位置開始搜尋字串。  如果未設定全域旗標，`exec` 則會略過 `lastIndex` 值，並從字串開頭開始搜尋。  
  
 `exec` 方法傳回的陣列有三種屬性：**input**、**index** 及 **lastIndex**。 **input** 屬性包含整個搜尋的字串。  **index** 屬性包含了在整個搜尋字串中相符子字串的位置。  `lastIndex` 屬性則包含了相符項目中跟著最後一個字元的位置。  
  
## 範例  
 在下列範例中，說明了如何使用 `exec` 方法：  
  
```javascript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + arr.lastIndex + " ");  
      document.write (arr[0]);  
      }  
}  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)  
  
## 請參閱  
 [match 方法 \(字串\)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp 物件](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-tw/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [search 方法 \(字串\)](../../javascript/reference/search-method-string-javascript.md)   
 [test 方法 \(規則運算式\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/zh-tw/3b62e27c-4f07-4726-a95b-6e841807bfaf)