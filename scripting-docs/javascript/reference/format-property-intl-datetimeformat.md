---
title: "format 屬性 (Intl.DateTimeFormat) | Microsoft Docs"
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
ms.assetid: 487930fe-a948-446f-902d-06bb0d7685d5
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# format 屬性 (Intl.DateTimeFormat)
傳回函式，透過使用指定的日期\/時間格式子設定，格式化地區設定特定的日期。  
  
## 語法  
  
```  
dateTimeFormatObj.format  
```  
  
#### 參數  
 `dateTimeFormatObj`  
 必要項。  做為格式子使用之 `DateTimeFormat` 物件的名稱。  
  
## 備註  
 `format` 屬性傳回的函式採用一個引數 `date`，並使用 `DateTimeFormat` 物件指定的選項，傳回代表當地語系化日期的字串。  所傳回函式的 `date` 參數必須是數字、日期字串或 `Date` 物件。  如果未提供 `date`，則函式會使用 [Date.now](../../javascript/reference/date-now-function-javascript.md) 做為預設輸入值。  
  
## 範例  
 下列範例會使用 `DateTimeFormat` 物件當地語系化日期 "Dec 1, 2007" 為德文和重新格式化文字。  
  
```javascript  
var dtFormat = new Intl.DateTimeFormat(["de"], {  
    year: "numeric",  
    month: "long",  
    day: "2-digit",  
    hour: "numeric"  
});  
  
if (console && console.log) {  
    console.log(dtFormat.format(new Date("Dec 1, 2007")));  
    // Returns 01. Dezember 2007 00:00  
}  
```  
  
## 需求  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 請參閱  
 [Intl.DateTimeFormat 物件](../../javascript/reference/intl-datetimeformat-object-javascript.md)