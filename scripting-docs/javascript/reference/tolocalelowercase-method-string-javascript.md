---
title: "toLocaleLowerCase 方法 (字串) (JavaScript) | Microsoft Docs"
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
  - "toLocaleLowerCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleLowerCase 方法"
ms.assetid: add894d3-d14a-4dbc-a9b9-7ad1d3a2e581
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# toLocaleLowerCase 方法 (字串) (JavaScript)
會將所有字母字元都轉換成小寫，並將主機環境的目前地區設定列入考慮。  
  
## 語法  
  
```  
  
stringVar.toLocaleLowerCase( )  
```  
  
## 備註  
 必要的 `stringVar` 參考是 `String` 物件或字串常值。  
  
 `toLocaleLowerCase` 方法會轉換字串中的字元，並將主機環境的目前地區設定列入考慮。  在大部分情況下，結果會和 `toLowerCase` 方法的結果相同。  但如果語言的規則與一般 Unicode 大小寫對應衝突，結果就會不同。  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用於**：[String 物件](../../javascript/reference/string-object-javascript.md)  
  
## 請參閱  
 [toLocaleUpperCase 方法 \(字串\)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [toLowerCase 方法](../../javascript/reference/tolowercase-method-javascript.md)