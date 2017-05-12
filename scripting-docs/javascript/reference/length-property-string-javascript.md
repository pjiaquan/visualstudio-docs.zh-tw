---
title: "length 屬性 (字串) (JavaScript) | Microsoft Docs"
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
  - "length Property"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "字串 [Visual Studio]，長度"
  - "Length 屬性"
  - "length 屬性 (字串)"
ms.assetid: 7dbd4a0e-c24e-4561-9b5b-e75e649a10a4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# length 屬性 (字串) (JavaScript)
傳回 `String` 物件的長度。  
  
> [!WARNING]
>  JavaScript 字串是不變的，因此無法修改字串的長度。  
  
## 語法  
  
```  
  
      strVariable.length  
"String Literal".length   
```  
  
## 備註  
 `length` 屬性包含可指出 `String` 物件中字元數的整數。  `String` 物件中最後一個字元的 i`length` 索引是 \-1。  
  
## 範例  
 在下列範例程式碼中，會示範 `length` 的用法。  JavaScript 字串是不變的，而且無法就地修改。  不過，您可以將反向字串寫入陣列，然後呼叫含空白字元的 `join`，它會產生不含分隔符號字元的字串。  
  
```javascript  
var str = "every good boy does fine";  
        var start = 0;  
        var end = str.length - 1;  
        var tmp = "";  
        var arr = new Array(end);  
  
        while (end >= 0) {  
            arr[start++] = str.charAt(end--);  
        }  
  
// Join the elements of the array with a   
        var str2 = arr.join('');  
        document.write(str2);  
  
// Output: enif seod yob doog yreve  
  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]