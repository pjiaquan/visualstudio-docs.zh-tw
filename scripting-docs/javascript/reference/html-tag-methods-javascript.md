---
title: "HTML 標記方法 (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "anchor 方法 [JavaScript]"
  - "big 方法 [JavaScript]"
  - "blink 方法 [JavaScript]"
  - "bold 方法 [JavaScript]"
  - "fixed 方法 [JavaScript]"
  - "fontcolor 方法 [JavaScript]"
  - "fontsize 方法 [JavaScript]"
  - "HTML 標記方法 [JavaScript]"
  - "italics 方法 [JavaScript]"
  - "link 方法 [JavaScript]"
  - "small 方法 [JavaScript]"
  - "sub 方法 [JavaScript]"
  - "sup 方法 [JavaScript]"
ms.assetid: 50376223-be95-4aa4-9147-9e738a5d3cfa
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# HTML 標記方法 (JavaScript)
在 `String` 物件中，您可以使用 HTML 標記方法，將 HTML 元素放在文字周圍。  
  
## 語法  
 下表列出每個 HTML 標記方法的語法和描述。  
  
 在語法資料行中，`string1` 是 `String` 物件或常值。  
  
 標準資料行會指示[全球資訊網協會 \(W3C\)](http://go.microsoft.com/fwlink/?LinkId=199553) 對於 HTML 4 的建議。  「不建議採用」表示為了樣式表而不建議使用此 HTML 元素。  
  
|語法|方法描述|參數描述|標準|  
|--------|----------|----------|--------|  
|`string1`.anchor\(`name`\)|將具有 NAME 屬性的 HTML 錨點放在文字周圍。|`name` 參數是放在 HTML 錨點之 NAME 屬性中的文字。||  
|`string1`.big\(\)|將 HTML \<BIG\> 標記放在文字周圍。||不建議採用|  
|`string1`.blink\(\)|將 HTML \<BLINK\> 標記放在文字周圍。  Internet Explorer 不支援 \<BLINK\> 標記。||非標準|  
|`string1`.bold\(\)|將 HTML \<B\> 標記放在文字周圍。||不建議採用|  
|`string1`.fixed\(\)|將 HTML \<TT\> 標記放在文字周圍。||不建議採用|  
|`string1`.fontcolor\(`color`\)|將具有 COLOR 屬性的 HTML \<FONT\> 標記放在文字周圍。|`color` 參數是一個字串值，其中包含色彩的十六進位值或預先定義的名稱。  有效的預先定義色彩名稱取決於 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 主瀏覽器和其版本。|已被取代的內容|  
|`string1`.fontsize\(`size`\)|將具有 SIZE 屬性的 HTML \<FONT\> 標記放在文字周圍。|`size` 參數是指定文字大小的整數值。  有效的整數值取決於 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 主瀏覽器和其版本。|已被取代的內容|  
|`string1`.italics\(\)|將 HTML \<I\> 標記放在文字周圍。||不建議採用|  
|`string1`.link\(`href`\)|將具有 HREF 屬性的 HTML 錨點放在文字周圍。|`href` 參數是放在 HTML 錨點之 HREF 屬性中的文字。||  
|`string1`.small\(\)|將 HTML \<SMALL\> 標記放在文字周圍。||不建議採用|  
|`string1`.strike\(\)|將 HTML \<STRIKE\> 標記放在文字周圍。||已被取代的內容|  
|`string1`.sub\(\)|將 HTML \<SUB\> 標記放在文字周圍。|||  
|`string1`.sup\(\)|將 HTML \<SUP\> 標記放在文字周圍。|||  
  
## 備註  
 不會執行任何檢查來判斷 HTML 標記是否已套用至字串。  
  
## 範例  
 下列範例示範如何使用 HTML 標記方法。  
  
```javascript  
// anchor method.  
var strVariable = "This is an anchor.";  
document.write(strVariable.anchor("Anchor1"));  
// Output: <A NAME="Anchor1">This is an anchor.</A>  
  
// big method.  
var strVariable = "This is a string.";  
document.write(strVariable.big());  
// Output: <BIG>This is a string.</BIG>  
  
//  blink method.  
var strVariable = "This is a string.";  
document.write(strVariable.blink());  
// Output: <BLINK>This is a string.</BLINK>  
  
//  bold method.  
var strVariable = "This is a string.";  
document.write(strVariable.bold());  
// Output: <B>This is a string.</B>  
  
//  fixed method.  
var strVariable = "This is a string.";  
document.write(strVariable.fixed());  
// Output: <TT>This is a string.</TT>  
  
//  fontcolor method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontcolor("red"));  
// Output: <FONT COLOR="red">This is a string.</FONT>  
  
//  fontsize method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontsize(-1));  
// Output: <FONT SIZE="-1">This is a string.</FONT>  
  
//  italics method  
var strVariable = "This is a string.";  
document.write(strVariable.italics());  
// Output: <I>This is a string.</I>  
  
//  link method.  
var strVariable = "This is a hyperlink.";  
document.write(strVariable.link("http://www.microsoft.com"));  
// Output: <A HREF="http://www.microsoft.com">This is a hyperlink.</A>  
  
//  small method.  
var strVariable = "This is a string.";  
document.write(strVariable.small());  
// Output: <SMALL>This is a string.</SMALL>  
  
//  strike method.  
var strVariable = "This is a string.";  
document.write(strVariable.strike());  
// Output: <STRIKE>This is a string.</STRIKE>  
  
//  sub method.  
var strVariable = "This is a string.";  
document.write(strVariable.sub());  
// Output: <SUB>This is a string.</SUB>  
  
//  sup method.  
var strVariable = "This is a string.";  
document.write(strVariable.sup());  
// Output: <SUP>This is a string.</SUP>  
```  
  
## 需求  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用於**：[String 物件](../../javascript/reference/string-object-javascript.md)  
  
## 請參閱  
 [String 物件](../../javascript/reference/string-object-javascript.md)