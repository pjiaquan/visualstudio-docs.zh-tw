---
title: "format 屬性 (Intl.NumberFormat) | Microsoft Docs"
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
ms.assetid: 68c3223a-023c-4fa0-aa99-d049a7a0e26a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# format 屬性 (Intl.NumberFormat)
傳回函式，透過使用指定的數字格式子設定，格式化地區設定特定的數字。  
  
## 語法  
  
```  
numberFormatObj.format  
```  
  
#### 參數  
 `numberFormatObj`  
 必要項。  做為格式子使用之 `NumberFormat` 物件的名稱。  
  
## 備註  
 `format` 屬性傳回的函式採用一個引數 `value`，並使用 `NumberFormat` 物件指定的選項，傳回代表當地語系化數字的字串。  如果未提供 `value`，則函式會傳回 `NaN` \(非數字\)。  
  
## 範例  
 下列範例使用 `NumberFormat` 物件來建立當地語系化的數字。  
  
```javascript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
})  
  
if (console && console.log) {  
    console.log(nf.format(100)); // "¥100.00"  
}  
  
```  
  
## 需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 請參閱  
 [Intl.NumberFormat 物件](../../javascript/reference/intl-numberformat-object-javascript.md)