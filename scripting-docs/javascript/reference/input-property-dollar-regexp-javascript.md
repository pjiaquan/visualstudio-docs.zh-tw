---
title: "input 屬性 ($_) (RegExp) (JavaScript) | Microsoft Docs"
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
  - "$_"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "$_ 屬性"
  - "input 屬性 ($_)"
ms.assetid: 88c6d1d8-56f7-4334-a7eb-e899aec9cda4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# input 屬性 ($_) (RegExp) (JavaScript)
傳回字串，規則運算式已根據此字串執行搜尋。  唯讀。  
  
## 語法  
  
```  
  
RegExp.input  
```  
  
## 備註  
 與這個屬性相關聯的物件一律為 `RegExp` 物件。  
  
 每當搜尋字串變更時，都會修改 **input** 屬性的值。  
  
 以下範例說明 **input** 屬性的用法：  
  
```javascript  
function inputDemo(){  
   var s;  
   var re = new RegExp("d(b+)(d)","ig");  
   var str = "cdbBdbsbdbdz";  
   var arr = re.exec(str);  
   s = "The string used for the match was " + RegExp.input;   
   return(s);  
}  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[RegExp 物件](../../javascript/reference/regexp-object-javascript.md)  
  
## 請參閱  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-tw/ab0766e1-7037-45ed-aa23-706f58358c0e)