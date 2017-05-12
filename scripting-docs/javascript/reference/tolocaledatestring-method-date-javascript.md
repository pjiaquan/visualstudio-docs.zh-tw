---
title: "toLocaleDateString 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "toLocaleDateString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleDateString 方法"
ms.assetid: 0b83715c-8ced-4bd7-8940-a8007d002d10
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# toLocaleDateString 方法 (日期) (JavaScript)
傳回的日期字串值是配合主機環境目前的地區設定或指定的地區設定 \(Locale\)。  
  
## 語法  
  
```  
  
dateObj.toLocaleDateString( [locales][, options])   
```  
  
#### 參數  
 `dateObj`  
 必要項。  `Date` 物件。  
  
 `locales`  
 選擇項。  包含一或多個語言或地區設定標記的地區設定字串的陣列。  如果包含多個地區設定的字串，以優先權的遞減順序列出這些字串，使第一個項目是慣用的地區設定。  如果省略這個參數，則會使用 JavaScript 執行階段的預設地區設定。  
  
 `options`  
 選擇項。  包含一個或多個指定比較選項之屬性的物件。  
  
## 備註  
 從 Internet Explorer 11 開始，`toLocaleDateString` 會在內部使用 `Intl.DateTimeFormat` 格式化日期，加入 `locales` 和 `options` 參數的支援。  如需有關這些參數的詳細資訊，請參閱 [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)。  
  
> [!IMPORTANT]
>  並非所有文件模式和瀏覽器版本都支援 `locales` 和 `options` 參數。  如需詳細資訊，請參閱＜需求＞一節。  
  
 當您在 Internet Explorer 10 標準文件模式、舊版的文件模式及 Qirks 模式使用 `toLocaleDateString` :  
  
-   它會傳回包含目前時區日期的字串值。  
  
-   傳回日期是採用主機環境目前地區設定的預設格式。  
  
 如果您省略 `locales` 參數，指令碼不能使用這個方法的傳回值來做判斷，因為它會因電腦而異。  在這個情節中，只使用方法來格式化顯示的文字 \(永不用於計算過程\)。  
  
## 範例  
 下列範例顯示如何使用 `toLocaleDateString` 方法與指定的地區設定和比較選項。  
  
```javascript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleDateString("ar-SA", options));  
document.write(date.toLocaleDateString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎   
// ‎2013‎年‎2‎月‎1‎日‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 `locales` 和 `options` 參數：  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 請參閱  
 [toDateString 方法 \(日期\)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [toLocaleTimeString 方法 \(日期\)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)