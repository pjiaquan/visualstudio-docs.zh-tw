---
title: "Array.from 函式 (陣列) (JavaScript) | Microsoft Docs"
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
ms.assetid: 1bf59a99-f860-4c4d-b4c6-d5f1f946a490
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Array.from 函式 (陣列) (JavaScript)
從陣列形式或遞迴物件傳回陣列。  
  
## 語法  
  
```  
Array.from (arrayLike [ , mapfn [ , thisArg ] ] );  
```  
  
#### 參數  
 `arrayLike`  
 必要項。  陣列型物件或遞迴物件。  
  
 `mapfn`  
 選擇項。  呼叫 `arrayLike` 中每個項目的對應函式。  
  
 `thisArg`  
 選擇項。  指定對應函式中的 `this` 物件。  
  
## 備註  
 `arrayLike` 參數必須是有索引項目的物件和 `length` 屬性或遞迴的物件，例如 `Set` 物件。  
  
 陣列中的每個項目上都會呼叫選用的對應函式。  
  
## 範例  
 下列範例從 DOM 項目節點的集合傳回陣列。  
  
```javascript  
var elemArr = Array.from(document.querySelectorAll('*'));  
var elem = elemArr[0]; // elem contains a reference to the first DOM element  
  
```  
  
## 範例  
 下列範例會傳回字元陣列。  
  
```javascript  
var charArr = Array.from("abc");  
// charArr[0] == "a";  
```  
  
## 範例  
 下列範例會傳回包含在集合中的物件陣列。  
  
```javascript  
var setObj = new Set("a", "b", "c");  
var objArr = Array.from(setObj);  
// objArr[1] == "b";  
  
```  
  
## 範例  
 下列範例顯示使用箭號語法和對應函式來變更項目的值。  
  
```javascript  
var arr = Array.from([1, 2, 3], x => x * 10);  
// arr[0] == 10;  
// arr[1] == 20;  
// arr[2] == 30;  
```  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]