---
title: "match 方法 (字串) (JavaScript) | Microsoft Docs"
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
  - "match"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Match 方法"
ms.assetid: eda9ad27-4f9b-4cb1-8345-a0ae85979ca0
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# match 方法 (字串) (JavaScript)
比對字串與規則運算式，然後傳回包含該搜尋結果的陣列。  
  
## 語法  
  
```  
  
stringObj.match(rgExp)   
```  
  
## 參數  
 `stringObj`  
 必要項。  要執行搜尋的 `String` 物件或字串常值 \(String Literal\)。  
  
 `rgExp`  
 必要項。  包含規則運算式模式及適用旗標的規則運算式物件。  這也可以是包含規則運算式模式與適用旗標的變數名稱或字串常值。  
  
## 備註  
 如果 `match` 方法找不到符合的項目，會傳回 `null`。  如果找到符合的項目，則 `match` 方法會傳回一個陣列，然後更新全域 `RegExp` 物件的屬性來反映符合的結果。  
  
 如果未設定全域旗標 \(`g`\)，陣列的元素 0 會包含整個相符項目，而元素 1 至 *n* 則包含任何子相符項目。  此行為相當於不設定全域旗標的 [exec 方法 \(規則運算式\)](../../javascript/reference/exec-method-regular-expression-javascript.md)。  如果設定全域旗標，元素 0 至 *n* 就會包含所有的相符項目。  
  
 如果未設定全域旗標，`match` 方法傳回的陣列有兩個屬性：`input` 和 `index`。  `input` 屬性包含整個搜尋的字串。  `index` 屬性包含相符子字串在整個搜尋字串中的位置。  
  
 如果設定旗標 `i`，則搜尋不區分大小寫。  
  
## 範例  
 在下列程式碼中，說明了如何使用 `match` 方法。  
  
```javascript  
var src = "azcafAJAC";  
  
var re = /[a-c]/;  
  
var result = src.match(re);  
  
// The entire match is in array element 0.  
document.write(result[0] + "<br/>");  
  
// Now try the same match with the global flag.  
var reg = /[a-c]/g;  
result = src.match(reg);  
  
// The matches are in elements 0 through n.  
for (var index = 0; index < result.length; index++)  
{  
    document.write ("submatch " + index + ": " +  result[index]);  
    document.write("<br />");  
}  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[String 物件](../../javascript/reference/string-object-javascript.md)  
  
## 請參閱  
 [exec 方法 \(規則運算式\)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [RegExp 物件](../../javascript/reference/regexp-object-javascript.md)   
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [replace 方法 \(字串\)](../../javascript/reference/replace-method-string-javascript.md)   
 [search 方法 \(字串\)](../../javascript/reference/search-method-string-javascript.md)   
 [test 方法 \(規則運算式\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/zh-tw/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternation and Subexpressions \(JavaScript\)](http://msdn.microsoft.com/zh-tw/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Backreferences \(JavaScript\)](http://msdn.microsoft.com/zh-tw/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)