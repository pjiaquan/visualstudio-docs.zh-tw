---
title: "prototype 屬性 (數字) | Microsoft Docs"
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
ms.assetid: d5fb87af-fc3a-4469-8dde-d31daf654f94
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype 屬性 (數字)
傳回數字類別的原型參考。  
  
## 語法  
  
```  
  
number.prototype  
```  
  
## 備註  
 `number` 引數是數字的名稱。  
  
 使用 `prototype` 屬性，將基本功能組提供給某一物件類別。  該物件的新執行個體都會「繼承」指定給該物件的原型行為。  
  
 例如，若要將方法加入至會傳回 \(整數\) 位數的 `Number` 物件，請宣告函式，並將它加入至 `Number.prototype`，然後使用它。  
  
```javascript  
function number_digits() {  
    var digits = 0;  
    var num = this;  
    while (num) >= 1) {  
        digits++;  
        num /= 10;  
    }  
    return digits;  
}  
  
Number.prototype.digits = number_digits;  
var myNumber = new Number(3456.789);  
document.write(myNumber.digits());  
// Output:  
// 4  
```  
  
 所有的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 內建物件都擁有一個唯讀的 `prototype` 屬性。  您可以為原型添加屬性和方法，但是無法為該內建物件指派不同的原型，  不過卻可以為使用者定義的物件指派新原型。  
  
 程式語言參考中會列出每個內建物件的方法和屬性，以標示哪些是物件原型的部分，以及哪些不是。  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]