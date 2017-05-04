---
title: "String.fromCharCode 函式 (JavaScript) | Microsoft Docs"
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
  - "fromCharCode"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "fromCharCodeAt 方法"
  - "字元，從 Unicode"
ms.assetid: f64120c1-23a7-48ca-8d1c-db3e8856cab4
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# String.fromCharCode 函式 (JavaScript)
傳回許多 Unicode 字元值中的字串。  
  
## 語法  
  
```  
String.fromCharCode([code1[, code2[, ...[, codeN]]]])   
```  
  
## 參數  
 `String`  
 必要項。  `String` 物件。  
  
 `code1`, . . . , `codeN`  
 選擇項。  轉換成字串的一連串 Unicode 字元值。  如果不提供引數，結果將是空字串。  
  
## 備註  
 您可以針對 `String` 物件 \(而不是字串執行個體\) 呼叫這個函式。  
  
 下列範例示範如何使用這個方法：  
  
```javascript  
var test = String.fromCharCode(112, 108, 97, 105, 110);  
document.write(test);  
  
// Output: plain  
  
```  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 請參閱  
 [charCodeAt 方法 \(字串\)](../../javascript/reference/charcodeat-method-string-javascript.md)