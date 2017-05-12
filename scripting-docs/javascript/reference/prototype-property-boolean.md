---
title: "prototype 屬性 (布林值) | Microsoft Docs"
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
ms.assetid: e4f07cb5-3462-488c-a418-76064ab10eae
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype 屬性 (布林值)
傳回布林原型的參考。  
  
## 語法  
  
```  
  
boolean.prototype  
```  
  
## 備註  
 `boolean` 引數是物件的名稱。  
  
 `prototype` 屬性提供某類別物件的一組基本功能。  物件的新執行個體會「繼承」指派給該物件之原型的行為。  屬性和方法可能會加入原型，但是內建物件可能未獲指派不同的原型。  
  
 例如，若要將方法加入可傳回陣列中最大項目值的 `Boolean` 物件，請宣告函式，並將它加入 `Boolean.prototype`，然後使用它。  
  
```javascript  
function isFalse( ){  
    if (this.toString() == "false")  
         return true;  
    else  
        return false;  
}  
Boolean.prototype.isFalse = isFalse;  
var bool = new Boolean(1);  
document.write(bool.isFalse());  
  
// Output:  
// false  
  
```  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]