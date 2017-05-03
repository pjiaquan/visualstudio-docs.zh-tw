---
title: "index 屬性 (RegExp) (JavaScript) | Microsoft Docs"
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
  - "index"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Index 屬性"
  - "比對字串"
ms.assetid: d8be1ef6-1bf2-43cd-b0b5-567a61eabaad
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# index 屬性 (RegExp) (JavaScript)
傳回字元位置，也就是第一個成功比對項目於搜尋字串的位置。  唯讀。  
  
## 語法  
  
```  
  
RegExp.index   
```  
  
## 備註  
 與這個屬性相關聯的物件一律為 `RegExp` 物件。  
  
 **index** 屬性以零為起始。  **index** 屬性的初始值是 –1。  無論何時只要比對成功，都會變更它的值。  
  
## 範例  
 以下範例說明 **index** 屬性的用法。  這個函式會重複搜尋字串，並印出字串中每個字的 **index** 和 `lastIndex` 值。  
  
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
      document.write (arr);  
      }  
}  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[RegExp 物件](../../javascript/reference/regexp-object-javascript.md)  
  
## 請參閱  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-tw/ab0766e1-7037-45ed-aa23-706f58358c0e)