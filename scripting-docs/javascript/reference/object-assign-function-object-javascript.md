---
title: "Object.assign 函式 (物件) (JavaScript) | Microsoft Docs"
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
ms.assetid: 2dd6b312-dcd3-414e-8d53-088c6341c46d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Object.assign 函式 (物件) (JavaScript)
將值從一或多個來源物件複製到目標物件。  
  
## 語法  
  
```  
Object.assign(target, ...sources );  
```  
  
#### 參數  
 `target`  
 必要項。  將可列舉屬性複製到其中的物件。  
  
 `...sources`  
 必要項。  從中複製可列舉屬性的一或多個物件。  
  
## 例外狀況  
 如果發生終止複製作業的指派錯誤，則此函式會擲回 `TypeError`。  如果目標屬性不可寫入，則會擲回 `TypeError`。  
  
## 備註  
 此函式會傳回目標物件。  只有*「可自行列舉」*\(Enumerable Own\) 屬性才能從來源物件複製到目標物件。  您可以使用此函式來合併或複製物件。  
  
 `null` 或 `undefined` 來源會被視為空物件，而且不會提供任何項目給目標物件。  
  
## 範例  
 下列程式碼範例示範如何使用 `Object.assign` 合併物件。  
  
```javascript  
var first = { name: "Bob" };  
var last = { lastName: "Smith" };  
  
var person = Object.assign(first, last);  
console.log(person);  
  
// Output:  
// { name: "Bob", lastName: "Smith" }   
```  
  
## 範例  
 下列範例示範如何使用 `Object.assign` 複製物件。  
  
```javascript  
var obj = { person: "Bob Smith"};  
var clone = Object.assign({}, obj);  
```  
  
## 需求  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]