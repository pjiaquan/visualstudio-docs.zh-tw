---
title: "toLocaleTimeString 方法 (日期) (JavaScript) | Microsoft Docs"
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
  - "toLocaleTimeString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleTimeString 方法"
ms.assetid: 8ad75bf5-864c-4a2a-be90-220e87dce172
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# toLocaleTimeString 方法 (日期) (JavaScript)
以字串值形式傳回適用於主機環境之目前地區設定或指定地區設定的時間。  
  
## 語法  
  
```  
  
dateObj.toLocaleTimeString([locales][, options])  
```  
  
#### 參數  
 `dateObj`  
 必要項。  `Date` 物件。  
  
 `locales`  
 選擇項。  包含一個或多個語言或地區設定標記的地區設定字串的陣列。  如果包含多個地區設定字串，請以優先權的遞減順序列出這些字串，讓第一個項目成為慣用的地區設定。  如果省略這個參數，則會使用 JavaScript 執行階段的預設地區設定。  
  
 `options`  
 選擇項。  一個物件，該物件包含一個或多個指定比較選項的屬性。  
  
## 備註  
 從 Internet Explorer 11 開始，`toLocaleTimeString` 在內部使用 `Intl.DateTimeFormat` 來格式化時間 \(這會加入 `locales` 和 `options` 參數的支援\)。  如需這些參數的詳細資訊，請參閱 [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md)。  
  
> [!IMPORTANT]
>  所有文件模式和瀏覽器版本都不支援 `locales` 和 `options` 參數。  如需詳細資訊，請參閱＜需求＞一節。  
  
 以 Internet Explorer 10 標準文件模式、舊版文件模式和快速模式使用 `toLocaleTimeString` 時：  
  
-   它會傳回內含目前時區時間的字串值。  
  
-   傳回的時間為主機環境之目前地區設定的預設格式。  
  
 如果您省略 `locales` 參數，這個方法的傳回值就不能依賴指令碼，因為它會因電腦不同而相異。  在此情況下，只使用方法來格式化顯示的文字 \(絕對不能是計算的一部分\)。  
  
## 範例  
 下列範例示範如何搭配使用 `toLocaleTimeString` 方法與指定的地區設定和比較選項。  
  
```javascript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleTimeString("en-US"));  
document.write(date.toLocaleTimeString("ja-JP"));  
document.write(date.toLocaleTimeString("ar-SA", options));  
document.write(date.toLocaleTimeString("hi-IN", options));  
  
// Output:  
// ‎‎6‎:‎00‎:‎00‎ ‎AM ‎   
// 6‎:‎00‎:‎00‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤ ٠٦‎:‎٠٠‎:‎٠٠‎ ‎ص  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013 06:00:00  
  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 `locales` 和 `options` 參數：  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 請參閱  
 [toTimeString 方法 \(日期\)](../../javascript/reference/totimestring-method-date-javascript.md)   
 [toLocaleDateString 方法 \(日期\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)