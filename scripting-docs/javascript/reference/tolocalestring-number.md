---
title: "toLocaleString (數字) | Microsoft Docs"
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
ms.assetid: 42c05252-13c1-4943-b1a4-b33285aeab3e
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# toLocaleString (數字)
使用目前或指定的地區設定，將數字轉換為字串。  
  
## 語法  
  
```  
  
numberObj.toLocaleString([locales][, options])   
```  
  
#### 參數  
 `numberObj`  
 必要項。  要進行轉換的 `Number` 物件。  
  
 `locales`  
 選擇項。  包含一或多個語言或地區設定標記的地區設定字串的陣列。  如果包含多個地區設定的字串，以優先權的遞減順序列出這些字串，使第一個項目是慣用的地區設定。  如果省略這個參數，則會使用 JavaScript 執行階段的預設地區設定。  
  
 `options`  
 選擇項。  包含一個或多個指定比較選項之屬性的物件。  
  
## 備註  
 從 Internet Explorer 11 開始，`toLocaleString` 會在內部使用 `Intl.NumberFormat` 進行比較，加入 `locales` 和 `options` 參數的支援。  如需有關這些參數的詳細資訊，請參閱 [Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md)。  
  
> [!IMPORTANT]
>  並非所有文件模式和瀏覽器版本都支援 `locales` 和 `options` 參數。  如需詳細資訊，請參閱＜需求＞一節。  
  
> [!NOTE]
>  如果您省略 `locales` 參數，請使用 `toLocaleString` 只顯示結果給使用者。請勿用來計算指令碼中的值，因為這個傳回的結果是電腦特定的值 \(方法會傳回目前的地區設定\)。  
  
## 範例  
 下列範例示範如何使用 `toLocaleString` 方法且不使用參數。  
  
```javascript  
var n, s;  
n = new Number(100);  
s = "Current locale value is: ";  
s += n.toLocaleString();                 
document.write(s);  
  
// Output:  
// The value 100 as represented by the current locale.  
```  
  
## 範例  
 下列範例顯示如何使用 `toLocaleString` 方法與指定的地區設定和比較選項。  
  
```javascript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
document.write(number.toLocaleString("en-US"));  
// 123,456,789  
document.write(number.toLocaleString("ja-JP"));  
// 123,456,789  
document.write(number.toLocaleString("ar-SA", options1));  
// ١٢,٣٤٥,٦٧٨,٩٠٠ %  
document.write(number.toLocaleString("hi-IN", options2));  
// ₹ 12,34,56,789.00  
  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 `locales` 和 `options` 參數：  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 請參閱  
 [toLocaleDateString 方法 \(日期\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)