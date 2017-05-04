---
title: "toLocaleString (日期) | Microsoft Docs"
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
ms.assetid: 3472d7bd-b255-4804-8407-c4a1e419a5a3
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# toLocaleString (日期)
使用目前或指定的地區設定，將日期轉換為字串。  
  
## 語法  
  
```  
  
dateObj.toLocaleString([locales][, options])   
```  
  
#### 參數  
 `dateObj`  
 必要項。  要進行轉換的 `Date` 物件。  
  
 `locales`  
 選擇項。  包含一或多個語言或地區設定標記的地區設定字串的陣列。  如果包含多個地區設定的字串，以優先權的遞減順序列出這些字串，使第一個項目是慣用的地區設定。  如果省略這個參數，則會使用 JavaScript 執行階段的預設地區設定。  
  
 `options`  
 選擇項。  包含一個或多個指定比較選項之屬性的物件。  
  
## 備註  
 從 Internet Explorer 11 開始，`toLocaleString` 會在內部使用 `Intl.DateTimeFormat` 進行比較，加入 `locales` 和 `options` 參數的支援。  如需有關這些參數的詳細資訊，請參閱 [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)。  
  
> [!IMPORTANT]
>  並非所有文件模式和瀏覽器版本都支援 `locales` 和 `options` 參數。  如需詳細資訊，請參閱＜需求＞一節。  
  
 當您在 Internet Explorer 10 標準文件模式、舊版的文件模式及 Qirks 模式使用 `toLocaleString` :  
  
-   它會傳回 `String` 物件，其中包含以目前地區設定的預設完整格式寫入的日期。  
  
-   對於西元 1601 到 1999 年之間的日期，會根據使用者的 \[控制台地區設定\] 設定日期格式。  
  
> [!NOTE]
>  如果您省略 `locales` 參數，請使用 `toLocaleString` 只顯示結果給使用者。請勿用來計算指令碼中的值，因為這個傳回的結果是電腦特定的值。  
  
## 範例  
 下列範例示範如何使用 `toLocaleString` 方法。  
  
```javascript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## 範例  
 下列範例顯示如何使用 `toLocaleString` 方法與指定的地區設定和比較選項。  
  
```javascript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleString("en-US"));  
document.write(date.toLocaleString("ja-JP"));  
document.write(date.toLocaleString("ar-SA", options));  
document.write(date.toLocaleString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎ ‎6‎:‎00‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎ ‎6‎:‎00‎:‎00  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 `locales` 和 `options` 參數：  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 請參閱  
 [toLocaleDateString 方法 \(日期\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)