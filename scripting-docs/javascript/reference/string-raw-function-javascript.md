---
title: "String.raw 函式 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b1038b73-3944-4645-b075-3a674b313762
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# String.raw 函式 (JavaScript)
傳回原始字串形式的範本字串。  
  
## 語法  
  
```  
String.raw`templateStr`;  
String.raw(obj, ...substitutions);  
```  
  
#### 參數  
 `templateStr`  
 必要項。  樣板字串。  
  
 `obj`  
 必要項。  使用物件常值標記法 \(例如 { raw: 'value' }\) 指定之語式正確的物件。  
  
 `...substitutions`  
 選擇項。  由一個或多個替代值組成的陣列 \([剩餘參數](../../javascript/functions-javascript.md)\)。  
  
## 備註  
 `String.raw` 函式可搭配[範本字串](../../javascript/advanced/template-strings-javascript.md)使用。  原始字串將會包含字串中的任何逸出字元和反斜線。  
  
 如果 `obj` 不是語式正確的物件，則會擲回錯誤。  
  
## 範例  
  
```  
function log(arg) {  
    if(console && console.log) {  
        console.log(arg);  
    }  
};  
  
var name = "bob";  
  
log(`hello \t${name}`);  
log(String.raw`hello \t${name}`);  
// The following usage for String.raw is supported but  
// is not typical.  
log(String.raw({ raw: 'fred'}, 'F', 'R', 'E'));  
  
// Output:  
// hello   bob  
// hello \tbob  
// fFrReEd  
  
```  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]