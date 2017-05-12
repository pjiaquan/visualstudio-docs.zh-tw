---
title: "toLowerCase 方法 (JavaScript) | Microsoft Docs"
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
  - "toLowerCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLowerCase 方法"
ms.assetid: dfd543b9-3e7a-4f83-a391-9cde109ad6bc
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# toLowerCase 方法 (JavaScript)
將字串中的所有字母字元轉換為小寫。  
  
## 語法  
  
```  
  
      strVariable.toLowerCase()  
"String Literal".toLowerCase()   
```  
  
## 備註  
 `toLowerCase` 方法對於非字母字元不會產生任何影響。  
  
 以下範例說明使用 `toLowerCase` 方法的效果：  
  
```javascript  
var str1 = "This is a STRING.";  
var str2 = str1. toLowerCase();  
document.write(str2);  
  
// Output: this is a string.  
  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[String 物件](../../javascript/reference/string-object-javascript.md)  
  
## 請參閱  
 [toLocaleLowerCase 方法 \(字串\)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [toUpperCase 方法 \(字串\)](../../javascript/reference/touppercase-method-string-javascript.md)