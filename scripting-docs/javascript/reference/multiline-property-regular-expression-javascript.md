---
title: "multiline 屬性 (規則運算式) (JavaScript) | Microsoft Docs"
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
  - "multiline"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "multiline 屬性"
ms.assetid: ca7b276a-1fe2-4189-ac27-f089ab3e9974
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# multiline 屬性 (規則運算式) (JavaScript)
傳回布林值，該值表示規則運算式所使用之 multiline 旗標 \(**m**\) 的狀態。  預設值為 **false**。  唯讀。  
  
## 語法  
  
```  
  
rgExp.multiline  
```  
  
## 備註  
 所需的 `rgExp` 引數是 `RegExp` 物件的執行個體。  
  
 如果已針對規則運算式設定 multiline 旗標，**multiline** 屬性會傳回 **true**，否則會傳回 **false**。  如果是以 **m** 旗標建立規則運算式物件，**multiline** 屬性為 **true**。  
  
 如果 **multiline** 是 **false**，"^" 會比對字串的開始位置，而 "$" 則會比對字串的結束位置。  如果 **multiline** 是 **true**，"^" 會比對字串的開始位置，以及 "\\n" 或 "\\r" 之後的位置，而 "$" 則會比對字串的結束位置，以及 "\\n" 或 "\\r" 之前的位置。  
  
## 範例  
 以下範例說明 **multiline** 屬性的行為。  如果您將 "m" 傳入以下顯示的函式，則會將單字 "while" 取代成 "and" 一字。  這是因為您設定了 multiline 旗標，而且單字 "while" 出現在新行字元後面的行首。  multiline 旗標可讓您對多行字串執行搜尋作業。  
  
```javascript  
function RegExpMultilineDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The man hit the ball with the bat ";  
   ss += "\nwhile the fielder caught the ball with the glove.";  
  
   // Replace "while" with "and".  
   var re = new RegExp("^while", flag);  
   var r = ss.replace(re, "and");          
  
   // Output the multiline flag and the resulting string.  
   var s = "";  
   s += "Result for multiline = " + re.multiline.toString();  
   s += ": " + r;  
  
   return(s);  
  
}  
  
sa = RegExpMultilineDemo("m");  
sb = RegExpMultilineDemo("");  
document.write (sa + "<br />" + sb);  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用於**：[規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)  
  
## 請參閱  
 [global 屬性 \(規則運算式\)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [ignoreCase 屬性 \(規則運算式\)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-tw/ab0766e1-7037-45ed-aa23-706f58358c0e)