---
title: "length 屬性 (函式) (JavaScript) | Microsoft Docs"
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
  - "Length 屬性"
  - "length 屬性 (函式)"
ms.assetid: fdc8e1c9-0dac-4e1b-ba3a-11073c37ef63
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# length 屬性 (函式) (JavaScript)
取得為某個函式所定義的引數個數。  
  
## 語法  
  
```  
  
functionName.length  
```  
  
## 備註  
 必要的 *functionName* 是函式的名稱。  
  
 建立函式的執行個體時，指令碼引擎會將函式中的 **length** 屬性初始化為此函式定義中的引數個數。  
  
 當函式使用與其 **length** 屬性值不同的引數個數來呼叫時，所發生的狀況視該函式而定。  
  
## 範例  
 以下範例說明 **length** 屬性的用法：  
  
```javascript  
function ArgTest(a, b){  
    var s = "";  
  
    s += "Expected Arguments: " + ArgTest.length;  
    s += "<br />";  
    s += "Passed Arguments: " + arguments.length;  
  
    return s;  
}  
  
document.write(ArgTest(1, 2));  
  
// Output:   
// Expected Arguments: 2  
// Passed Arguments: 2  
  
```  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## 請參閱  
 [arguments 屬性 \(函式\)](../../javascript/reference/arguments-property-function-javascript.md)   
 [length 屬性 \(陣列\)](../../javascript/reference/length-property-array-javascript.md)   
 [length 屬性 \(字串\)](../../javascript/reference/length-property-string-javascript.md)