---
title: "undefined 常數 (JavaScript) | Microsoft Docs"
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
  - "undefined"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "undefined 屬性"
ms.assetid: 2a689d7d-00b0-48fb-9c95-5c2867bde006
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# undefined 常數 (JavaScript)
從未定義的值，例如尚未初始化的變數。  
  
## 語法  
  
```  
undefined  
```  
  
## 備註  
 `undefined` 常數是 `Global` 物件的成員，並且會在指令碼引擎初始化時成為可用。  只經過宣告，但尚未初始化的變數，它的值是 **undefined**。  
  
 如果是未經過宣告的變數，您就無法將它與 `undefined` 比較，但可以將變數的型別與 "undefined" 字串比較。  
  
 要明確測試變數或將變數設定為 undefined 時，`undefined` 常數會很有幫助。  
  
## 範例  
 下列範例示範如何使用 `undefined` 常數。  
  
```javascript  
// A variable that has not been initialized.  
var declared;  
  
if (declared == undefined)  
    document.write("declared has not been given a value <br/>");  
else  
    document.write("declared has been given a value <br/>");  
  
document.write("typeof declared is " + typeof(declared) + "<br/>");  
  
// An undeclared variable cannot be compared to undefined,  
// so the next line would generate an error.  
// if (notDeclared == undefined);  
  
document.write("typeof notDeclared is " + typeof(notDeclared));  
  
// Output:  
// declared has not been given a value  
// typeof declared is undefined  
// typeof notDeclared is undefined  
```  
  
## 需求  
 在 [!INCLUDE[jsv55text](../../javascript/reference/includes/jsv55text-md.md)] 中就已經使用 `undefined` 屬性，而且在 [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)]中更成為了唯讀屬性。  
  
 **適用於**：[Global 物件](../../javascript/reference/global-object-javascript.md)  
  
## 請參閱  
 [typeof 運算子](../../javascript/reference/typeof-operator-decrementjavascript.md)