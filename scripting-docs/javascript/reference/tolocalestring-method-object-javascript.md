---
title: "toLocaleString 方法 (Object) (JavaScript) | Microsoft Docs"
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
  - "toLocaleString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleString 方法"
ms.assetid: 0901afcb-126b-4ed7-bd6a-2301d50e2326
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toLocaleString 方法 (Object) (JavaScript)
傳回使用目前的地區設定轉換為字串的日期。  
  
## 語法  
  
```  
  
dateObj.toLocaleString()   
```  
  
## 備註  
 必要的 `dateObj` 可以是任何 `Date` 物件。  
  
 `toLocaleString` 方法會傳回 `String` 物件，其中包含以目前地區設定的預設長格式所寫入的日期。  
  
-   如果日期介於西元 1601 到 1999 年之間，其格式將視使用者電腦 \[控制台\] 內的 \[地區設定\] 而定。  
  
-   如果是超出這個範圍以外的日期，則會使用 **toString** 方法的預設格式。  
  
 例如在美國，`toLocaleString` 針對 1 月 5 日這個日期轉換後會傳回 "01\/05\/96 00:00:00"。  相同日期如果地區是歐洲，則會傳回 "05\/01\/96 00:00:00"，因為當地的日期設定習慣將日期置於月份之前。  
  
> [!NOTE]
>  `toLocaleString` 應只用於顯示結果讓使用者查看，不應當成指令碼的計算基準，因為傳回的結果會因電腦的不同而有差異。  
  
## 範例  
 在下列範例中，說明了如何使用 `toLocaleString` 方法。  
  
```javascript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[Array 物件](../../javascript/reference/array-object-javascript.md)&#124; [Date 物件](../../javascript/reference/date-object-javascript.md)&#124; [Number 物件](../../javascript/reference/number-object-javascript.md)&#124; [Object 物件](../../javascript/reference/object-object-javascript.md)  
  
## 請參閱  
 [toLocaleDateString 方法 \(日期\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)