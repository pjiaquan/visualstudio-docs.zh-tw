---
title: "規則運算式物件 (JavaScript) | Microsoft Docs"
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
  - "RegularExpression_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "RegExp 物件, 概觀"
  - "規則運算式物件"
  - "規則運算式, RegExp 物件"
ms.assetid: 346aa83e-a045-47ea-acae-b42c7b121534
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# 規則運算式物件 (JavaScript)
此物件包含規則運算式模式，以及指出如何套用該模式的旗標。  
  
## 語法  
  
```  
re = /pattern/[flags]  
```  
  
## 語法  
  
```  
re = new RegExp("pattern"[,"flags"])   
```  
  
## 參數  
 *re*  
 必要項。  要指派以此規則運算式模式的變數名稱。  
  
 *pattern*  
 必要項。  要使用的規則運算式模式。  如果您使用語法 1，請使用 "\/" 字元分隔模式。  如果您使用語法 2，請使用引號括住模式。  
  
 `flags`  
 選擇項。  如果您使用語法 2，請使用引號括住旗標。  可用的旗標 \(可能已合併\) 如下：  
  
-   g \(全域搜尋所有出現的 *pattern*\)  
  
-   i \(忽略大小寫\)  
  
-   m \(多行搜尋\)  
  
-   u \(Unicode\)，會啟用 EcmaScript 6 [Unicode 功能](../../javascript/advanced/special-characters-javascript.md)。  僅適用於 [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)]。  
  
-   y \(原地搜尋\)，只在規則運算式的 `lastIndex` 屬性中搜尋相符的項目 \(而不繼續搜尋後續的索引\)。  適用於 [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)]。  
  
## 備註  
 **規則運算式**物件不應與全域 `RegExp` 物件混淆。  兩者看似相同，但卻完全不同。  **規則運算式**物件的屬性只會包含一個特定**規則運算式**執行個體的資訊，而全域 `RegExp` 物件的屬性則包含每個相符項目的資訊，並會隨著每次找到而持續更新。  
  
 **規則運算式**物件會儲存搜尋字串，以找出字元組合時所使用的模式。  **規則運算式**物件在建立之後會傳遞給字串方法，或將字串傳遞給其中一種規則運算式方法。  最近執行之搜尋的相關資訊會儲存在全域 `RegExp` 物件中。  
  
 如果您已經知道搜尋字串，請使用語法 1。  如果搜尋字串經常變更或不明 \(例如來自使用者輸入的字串\)，請使用語法 2。  
  
 *pattern* 引數在使用之前，會先編譯成內部格式。  在語法 1 中，*pattern* 會在載入指令碼時編譯。  在語法 2 中，只有在使用或呼叫 **compile** 方法時，才會編譯 *pattern*。  
  
## 範例  
 下列範例示範如何建立物件 \(re\) 包含規則運算式模式及其相關聯的旗標，以使用**規則運算式**物件。  在此案例中，`match` 方法會使用所產生的**規則運算式**物件：  
  
```javascript  
var s = "through the pages of the book";  
  
// Create regular expression pattern.  
var re = new RegExp("the", "i");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return first occurrence of "the".  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
//   
```  
  
## 範例  
 下列範例會更新規則運算式模式，以搜尋多個執行個體。  
  
```javascript  
// Create regular expression pattern using the i and g flags.  
var re = new RegExp("the", "ig");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return the two occurrences of "the".  
if(console && console.log) {  
    console.log(r.length);  
    console.log(r);  
}  
  
// Output:  
// 2  
// [object Array] ["the", "the"]  
```  
  
## 範例  
 使用 \/y 旗標時，如果搜尋成功，將會在搜尋到最後一個相符項目之後，將 `lastindex` 更新為下一個字元的索引。  如果搜尋失敗，會將 `lastindex` 重設為 0。  
  
 下列範例會使用 \/y 旗標及 `lastIndex` 屬性，在特定索引中搜尋相符項目。  
  
```javascript  
// Create regular expression pattern using the i and y flags.  
var re = new RegExp("the", "iy");  
  
// Set the lastIndex property and attempt a match  
// at the specified index.  
re.lastIndex = 20;  
var r = s.match(re);     
  
// No matches returned.  
if(console && console.log) {  
    console.log(r);  
}  
// Reset the lastIndex property and attempt a match.  
re.lastIndex = 21;  
var r = s.match(re);  
  
// Return occurrence of "the" starting at index 21.  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
// null  
// [object Array] ["the"]  
```  
  
<a name="js56jsobjregexpressionprop"></a>   
## 屬性  
 [global 屬性](../../javascript/reference/global-property-regular-expression-javascript.md) &#124; [ignoreCase 屬性](../../javascript/reference/ignorecase-property-regular-expression-javascript.md) &#124; [multiline 屬性](../../javascript/reference/multiline-property-regular-expression-javascript.md) &#124; [source 屬性](../../javascript/reference/source-property-regular-expression-javascript.md)  
  
<a name="js56jsobjregexpressionmeth"></a>   
## 方法  
 [compile 方法](../../javascript/reference/compile-method-regular-expression-javascript.md) &#124; [exec 方法](../../javascript/reference/exec-method-regular-expression-javascript.md) &#124; [test 方法](../../javascript/reference/test-method-regular-expression-javascript.md)  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 u 旗標適用於 [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)]。  
  
 y 旗標適用於 [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)]。  
  
## 請參閱  
 [RegExp 物件](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-tw/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String 物件](../../javascript/reference/string-object-javascript.md)