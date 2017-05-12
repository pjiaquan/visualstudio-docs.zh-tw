---
title: "localeCompare 方法 (字串) (JavaScript) | Microsoft Docs"
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
  - "localeCompare"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "localeCompare 方法"
ms.assetid: 66914079-12dd-4393-a84c-c05f58231c36
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# localeCompare 方法 (字串) (JavaScript)
判斷在目前地區設定中兩個字串是否相等。  
  
## 語法  
  
```  
  
stringVar.localeCompare(stringExp[, locales][, options])   
```  
  
## 參數  
 `stringVar`  
 必要項。  要比較的第一個字串。  
  
 `stringExp`  
 必要項。  要比較的第二個字串。  
  
 `locales`  
 選擇項。  包含一或多個語言或地區設定標記的地區設定字串的陣列。  如果包含多個地區設定的字串，以優先權的遞減順序列出這些字串，使第一個項目是慣用的地區設定。  如果省略這個參數，則會使用 JavaScript 執行階段的預設地區設定。  這個參數必須符合 [BCP 47](http://tools.ietf.org/html/rfc5646) 標準；請參閱 [Intl.Collator 物件](../../javascript/reference/intl-collator-object-javascript.md)以取得詳細資訊。  
  
 `options`  
 選擇項。  包含一個或多個指定比較選項之屬性的物件。如需詳細資訊，請參閱 [Intl.Collator object](../../javascript/reference/intl-collator-object-javascript.md)。  
  
## 備註  
 若為比較字串，您可以指定 `String` 物件或字串常值。  
  
 從 Internet Explorer 11 開始，`localeCompare` 會在內部使用 `Intl.Collator` 物件進行比較，加入 `locales` 和 `options` 參數的支援。  如需這些參數的詳細資訊，請參閱 [Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md) 和 [Intl.Collator.compare](../../javascript/reference/compare-property-intl-collator.md)。  
  
> [!IMPORTANT]
>  並非所有文件模式和瀏覽器版本都支援 `locales` 和 `options` 參數。  如需詳細資訊，請參閱＜需求＞一節。  
  
 `localeCompare` 方法會針對 `stringVar` 和 `stringExp` 執行區分地區設定的比較，並且根據系統預設地區設定的排序次序傳回下列結果：  
  
-   如果 `stringExp` 排序在 `stringVar` 之前，則為 \-1。  
  
-   如果 `stringVar` 排序在 `stringExp` 之後，則為 \+1。  
  
-   如果兩個字串相等，則為 0 \(零\)。  
  
## 範例  
 下列程式碼示範 `localeCompare` 的用法。  
  
```javascript  
var str1 = "def";  
var str2 = "abc"  
  
document.write(str1.localeCompare(str2) + "<br/>");  
  
// Output: 1  
var str3 = "ghi";  
  
document.write(str1.localeCompare(str3)+ "<br/>");  
  
// Output: -1  
var str4 = "def";  
  
document.write(str1.localeCompare(str4));  
  
// Output: 0  
```  
  
## 範例  
 下列程式碼示範如何使用 `localeCompare` 與德文 \(德國\) 地區設定。  
  
```javascript  
var str1 = "a";  
var str2 = "b";  
  
document.write(str1.localeCompare(str2, "de-DE"));  
  
// Output  
// - 1  
```  
  
## 範例  
 下列範例顯示如何使用 `localeCompare`、德文 \(德國\) 地區設定和為德文電話簿指定排序次序的地區設定特定擴充功能。  這個範例示範地區設定特定的差異。  
  
```javascript  
var arr = ["ä", "ad", "af", "a"];  
  
document.write(arr[0].localeCompare(arr[1], "de-DE-u-co-phonebk"));  // Returns 1  
document.write (arr[0].localeCompare(arr[2], "de-DE-u-co-phonebk"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE-u-co-phonebk"));  // Returns 1  
  
document.write (arr[0].localeCompare(arr[1], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[2], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE"));  // Returns 1  
  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 `locales` 和 `options` 參數：  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 請參閱  
 [toLocaleString 方法 \(Object\)](../../javascript/reference/tolocalestring-method-object-javascript.md)