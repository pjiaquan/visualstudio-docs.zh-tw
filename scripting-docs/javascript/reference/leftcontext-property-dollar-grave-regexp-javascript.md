---
title: "leftContext 屬性 ($`) (RegExp) (JavaScript) | Microsoft Docs"
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
  - "$`"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "leftContext 屬性 ($`)"
ms.assetid: 840e56c0-eb7c-461f-bb56-91acff9b5bcf
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# leftContext 屬性 ($`) (RegExp) (JavaScript)
傳回從搜尋字串開頭，一直到上次符合項目開頭的前一個位置的字元。  唯讀。  
  
## 語法  
  
```  
  
RegExp.leftContext  
```  
  
## 備註  
 與這個屬性相關聯的物件一律為 `RegExp` 物件。  
  
 `leftContext` 屬性的初始值是空字串。  每次比對成功時，`leftContext` 屬性的值就會變更。  
  
## 範例  
 下列範例說明 `leftContext` 屬性的使用方式：  
  
```javascript  
// Create the regular expression pattern.  
var re = new RegExp("d(b+)(d)","ig");  
var str = "cdbBdbsbdbdz";  
  
// Perform the search.  
var arr = re.exec(str);  
  
// Print the output.  
var s = ""   
s += "$1: " + RegExp.$1 + "<br />";  
s += "$2: " + RegExp.$2 + "<br />";  
s += "$3: " + RegExp.$3 + "<br />";  
s += "input: " + RegExp.input + "<br />";  
s += "lastMatch: " + RegExp.lastMatch + "<br />";  
s += "leftContext: " + RegExp.leftContext + "<br />";  
s += "rightContext: " + RegExp.rightContext + "<br />";   
s += "lastParen: " + RegExp.lastParen + "<br />";  
  
document.write(s);  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用於**：[RegExp 物件](../../javascript/reference/regexp-object-javascript.md)  
  
## 請參閱  
 [$1...$9 屬性 \(RegExp\)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)   
 [index 屬性 \(RegExp\)](../../javascript/reference/index-property-regexp-javascript.md)   
 [input 屬性 \($\_\) \(RegExp\)](../../javascript/reference/input-property-dollar-regexp-javascript.md)   
 [lastIndex 屬性 \(RegExp\)](../../javascript/reference/lastindex-property-regexp-javascript.md)   
 [lastMatch 屬性 \($&\) \(RegExp\)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)   
 [lastParen 屬性 \($\+\) \(RegExp\)](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)   
 [rightContext 屬性 \($'\) \(RegExp\)](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)