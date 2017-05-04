---
title: "prototype 屬性 (陣列) | Microsoft Docs"
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
ms.assetid: 5fedf632-8316-4e5d-ab20-10e41aa4d9f8
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype 屬性 (陣列)
傳回陣列類別的原型參考。  
  
## 語法  
  
```  
  
array.prototype  
```  
  
## 備註  
 `array` 引數是陣列的名稱。  
  
 使用 `prototype` 屬性，將基本功能組提供給某一物件類別。  該物件的新執行個體都會「繼承」指定給該物件的原型行為。  
  
 例如，若要將方法加入至 `Array` 物件 \(此方法會傳回最大陣列元素的值\)，請宣告函式，並將它加入至 `Array.prototype`，然後使用它。  
  
```javascript  
function array_max( ){  
    var i, max = this[0];  
    for (i = 1; i < this.length; i++)  
    {  
    if (max < this[i])  
    max = this[i];  
    }  
    return max;  
}  
Array.prototype.max = array_max;  
var myArray = new Array(7, 1, 3, 11, 25, 9  
);  
document.write(myArray.max());  
  
// Output: 25  
```  
  
 所有的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 內建物件都擁有一個唯讀的 `prototype` 屬性。  您可以為原型添加屬性和方法，但是無法為該內建物件指派不同的原型，  不過卻可以為使用者定義的物件指派新原型。  
  
 程式語言參考中會列出每個內建物件的方法和屬性，以標示哪些是物件原型的部分，以及哪些不是。  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]