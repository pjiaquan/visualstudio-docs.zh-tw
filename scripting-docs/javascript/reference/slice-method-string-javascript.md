---
title: "slice 方法 (字串) (JavaScript) | Microsoft Docs"
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
  - "slice"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "slice 方法"
  - "字串 [Visual Studio], 傳回字元"
ms.assetid: 80cd77a6-3718-492e-8e96-f909d8721d91
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# slice 方法 (字串) (JavaScript)
傳回字串的一個區段。  
  
## 語法  
  
```  
  
stringObj.slice(start, [end])   
```  
  
## 參數  
 `stringObj`  
 必要項。  `String` 物件或字串常值。  
  
 `start`  
 必要項。  `stringObj` 之指定部分開頭的索引。  
  
 `end`  
 選擇項。  `stringObj` 之指定部分結尾的索引。  此子字串包含的字元一直到 \(但不包括\) `end` 所指定的字元。  如果未指定這個值，子字串會一直持續到 `stringObj` 的結尾。  
  
## 備註  
 `slice` 方法會傳回 `String` 物件，其中包含 `stringObj` 的指定部分。  
  
 `slice` 方法會複製字元，一直到 `end` 所表示的字元，但不包括此字元。  
  
 如果 `start` 是負值，則這個值會被視為是 *length* \+ `start`，其中 *length* 是這個字串的長度。  如果 `end` 是負數，表示將其視為 *length* \+ `end`。  如果省略 `end`，就會繼續複製，一直到 `stringObj` 的結尾。  如果 `end` 出現在 `start` 之前，則將不會複製任何字元到新字串之中。  
  
## 範例  
 在第一個範例中，`slice` 方法會傳回整個字串。  在第二個範例中，`slice` 方法會傳回整個字串，但最後一個字元除外。  
  
```javascript  
var str1 = "all good boys do fine";  
  
var slice1 = str1.slice(0);  
var slice2 = str1.slice(0,-1);  
var slice3 = str1.slice(4);  
var slice4 = str1.slice(4, 8);  
  
document.write(slice1 + "<br/>");  
document.write(slice2 + "<br/>");  
document.write(slice3 + "<br/>");  
document.write(slice4);  
  
// Output:  
// all good boys do fine  
// all good boys do fin  
// good boys do fine  
// good  
  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用於**：[String 物件](../../javascript/reference/string-object-javascript.md)  
  
## 請參閱  
 [slice 方法 \(陣列\)](../../javascript/reference/slice-method-array-javascript.md)