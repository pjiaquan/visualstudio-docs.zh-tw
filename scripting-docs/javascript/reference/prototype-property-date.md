---
title: "prototype 屬性 (日期) | Microsoft Docs"
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
ms.assetid: 44f9c637-7da7-4833-906d-358506f32ced
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# prototype 屬性 (日期)
傳回日期物件的原型參考。  
  
## 語法  
  
```  
  
date.prototype  
```  
  
## 備註  
 `date` 引數是物件的名稱。  
  
 您可以使用 `prototype` 屬性提供 Date 物件的基本功能集。  該物件的新執行個體都會「繼承」指定給該物件的原型行為。  
  
 例如，若要為 `Date` 物件添加方法 \(此方法會傳回陣列中最大元素的值\)，請宣告函式，並將它加入至 `Date.prototype`，然後使用它。  
  
```javascript  
function max( ){  
    var max = new Date();  
    max.setFullYear(2200, 01, 01);  
    return max;  
}  
Date.prototype.maxDate = max;  
var myDate = new Date();  
  
if (myDate < myDate.maxDate())  
    document.write("today isn't the max");  
else if (myDate == myDate.maxDate())  
    document.write("today is the max");   
  
// Output:  
// today isn't the max  
  
```  
  
 所有的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 內建物件都擁有一個唯讀的 `prototype` 屬性。  您可以為原型添加屬性和方法，但是無法為該內建物件指派不同的原型，  不過卻可以為使用者定義的物件指派新原型。  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]