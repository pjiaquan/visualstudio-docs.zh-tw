---
title: "prototype 屬性 (錯誤) | Microsoft Docs"
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
ms.assetid: 6c268a51-1a3d-4397-abf8-e54ca4e598fe
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# prototype 屬性 (錯誤)
傳回錯誤的原型參考。  
  
## 語法  
  
```  
  
error.prototype  
```  
  
## 備註  
 `error` 引數是錯誤的名稱。  
  
 您可以使用 `prototype` 屬性提供 Error 物件的基本功能集。  該物件的新執行個體都會「繼承」指定給該物件的原型行為。  
  
 例如，若要將方法加入至 `Error` 物件 \(此方法會傳回最大陣列元素的值\)，請宣告函式，並將它加入至 `Error.prototype`，然後使用它。  
  
```javascript  
function getSeverity(){  
    if (this.number > 1000)  
        return "high";  
    else  
        return "low";  
}  
Error.prototype.getSev = getSeverity;  
var myError = new Error();  
myError.number = 5000;  
  
document.write(myError.getSev());   
  
// Output: high  
  
```  
  
 所有的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 內建物件都擁有一個唯讀的 `prototype` 屬性。  您可以為原型添加屬性和方法，但是無法為該內建物件指派不同的原型，  不過卻可以為使用者定義的物件指派新原型。  
  
## 需求  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]