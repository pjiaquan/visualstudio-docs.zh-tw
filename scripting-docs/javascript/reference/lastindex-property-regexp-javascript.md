---
title: "lastIndex 屬性 (RegExp) (JavaScript) | Microsoft Docs"
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
  - "lastIndex"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lastIndex 屬性"
ms.assetid: c8ae2a13-6dff-4cbe-b662-aca3d66c2a7f
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# lastIndex 屬性 (RegExp) (JavaScript)
傳回字元位置，代表搜尋字串中下一個符合的位置。  
  
## 語法  
  
```  
  
RegExp.lastIndex  
```  
  
## 備註  
 與這個屬性相關聯的物件永遠為 `RegExp` 物件。  
  
 `lastIndex` 屬性以零為起始，亦即第一個字元的索引為零。  它的初始值為 –1。  無論何時只要成功符合，都會修改它的值。  
  
 `lastIndex` 屬性是由 `RegExp` 物件的 `exec` 和 **test** 方法及 `String` 物件的 `match`、**replace** 和 **split** 方法所修改。  
  
 以下規則套用到 `lastIndex` 的值：  
  
-   如果比對失敗，`lastIndex` 會設為 \-1。  
  
-   如果 `lastIndex` 大於字串的長度，**test** 和 `exec` 會失敗，且 `lastIndex` 會設為 \-1。  
  
-   如果 `lastIndex` 等於字串的長度，則規則運算式會在模式符合空字串時與其相符。  否則，比對將失敗，且 `lastIndex` 會重設為 \-1。  
  
-   否則，`lastIndex` 會設為最近一次比對成功項目的下一個位置。  
  
## 範例  
 下列範例說明 `lastIndex` 屬性的使用方式。  這個函式會重複搜尋字串，並印出字串中每個字的 **index** 和 `lastIndex` 值。  
  
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
      document.write (arr.index + "-" + re.lastIndex + " ");  
      document.write (arr);  
      }  
}  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[RegExp 物件](../../javascript/reference/regexp-object-javascript.md)  
  
## 請參閱  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-tw/ab0766e1-7037-45ed-aa23-706f58358c0e)