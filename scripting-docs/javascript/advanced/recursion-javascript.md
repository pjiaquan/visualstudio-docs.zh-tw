---
title: "遞迴 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "函式，遞迴函式呼叫"
  - "遞迴程序"
  - "函式呼叫，遞迴"
ms.assetid: 885855a6-3838-457d-9eb4-cce1ccaa5a8d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# 遞迴 (JavaScript)
遞迴是一種重要的程式設計技巧，可以使函式呼叫其本身。  
  
## 遞迴的範例  
 階乘計算就是一個例子。  數字之階乘 *n* 是藉由乘以 1 \* 2 \* 3 \*…  *n* 來計算。  下列範例示範如何反覆計算階乘，亦即，您可以使用會計算結果的 `while` 迴圈。  
  
```javascript  
function factorial(num)  
{  
    // If the number is less than 0, reject it.  
    if (num < 0) {  
        return -1;  
    }  
    // If the number is 0, its factorial is 1.  
    else if (num == 0) {  
        return 1;  
    }  
    var tmp = num;  
    while (num-- > 2) {  
        tmp *= num;  
    }  
    return tmp;  
}  
  
var result = factorial(8);  
document.write(result);  
  
// Output: 40320  
```  
  
 您可以很容易就讓此範例遞迴。  除了使用 `while` 迴圈計算值，您可以簡單地再次呼叫 `factorial`，傳入下一個最小的值。  當值為 1 時，遞迴就會停止。  
  
```javascript  
function factorial(num)  
{  
    // If the number is less than 0, reject it.  
    if (num < 0) {  
        return -1;  
    }  
    // If the number is 0, its factorial is 1.  
    else if (num == 0) {  
        return 1;  
    }  
    // Otherwise, call this recursive procedure again.  
    else {  
        return (num * factorial(num - 1));  
    }  
}  
  
var result = factorial(8);  
document.write(result);  
  
// Output: 40320  
```