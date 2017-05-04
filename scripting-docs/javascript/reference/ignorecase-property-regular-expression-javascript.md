---
title: "ignoreCase 屬性 (規則運算式) (JavaScript) | Microsoft Docs"
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
  - "ignoreCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "IgnoreCase 屬性"
ms.assetid: 816f0df5-5a82-44a5-a4ab-dbc91fa76e61
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# ignoreCase 屬性 (規則運算式) (JavaScript)
傳回布林值，該值表示搭配規則運算式所使用之 ignoreCase 旗標 \(**i**\) 的狀態。  預設值為 **false**。  唯讀。  
  
## 語法  
  
```  
  
rgExp.ignoreCase  
```  
  
## 備註  
 所需的 `rgExp` 參考是 `RegExp` 物件的執行個體。  
  
 如果已針對規則運算式設定 ignoreCase 旗標，**ignoreCase** 屬性會傳回 **true**，否則會傳回 **false**。  
  
 若使用 ignoreCase 旗標，表示搜尋功能在搜尋字串內比對模式時應該不區分大小寫。  
  
## 範例  
 以下範例示範 **ignoreCase** 屬性的用法。  如果您將 "gi" 傳入下列顯示的函式，則會將所有的單字 "the" 全部取代成 "a" 這個字，包括句首的 "The"。  這是因為設定 ignoreCase 旗標後，搜尋便會忽略任何大小寫。  因此，就比對目的來說，"T" 與 "t" 相同。  
  
 這個函式會傳回布林值，該值表示允許之規則運算式旗標 \(包括 **g**、**i** 和 **m**\) 的狀態。  此函式也會傳回已完成所有取代的字串。  
  
```javascript  
function RegExpPropDemo(flag){  
    // The flag parameter is a string that contains  
    // g, i, or m. The flags can be combined.  
  
    // Check flags for validity.  
    if (flag.match(/[^gim]/))  
        {  
        return ("Flag specified is not valid");  
        }  
  
    // Create the string on which to perform the replacement.  
    var orig = "The batter hit the ball with the bat ";  
    orig += "and the fielder caught the ball with the glove.";  
  
    // Replace "the" with "a".  
    var re = new RegExp("the", flag);  
    var r = orig.replace(re, "a");          
  
    // Output the resulting string and the values of the flags.  
    var s = "";  
    s += "global: " + re.global.toString();  
    s += "<br />";  
    s += "ignoreCase: " + re.ignoreCase.toString();  
    s += "<br />";  
    s += "multiline: " + re.multiline.toString();  
    s += "<br />";  
    s += "Resulting String: " + r;  
    s += "<br />";  
    s += "<br />";  
    return (s);  
}  
  
document.write(RegExpPropDemo("gi"));  
document.write(RegExpPropDemo("g"));  
```  
  
## 範例  
 下列是產生的輸出。  
  
```javascript  
global: true  
ignoreCase: true  
multiline: false  
Resulting String: a batter hit a ball with a bat and a fielder caught a ball with a glove.  
  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用於**：[規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)  
  
## 請參閱  
 [global 屬性 \(規則運算式\)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [multiline 屬性 \(規則運算式\)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-tw/ab0766e1-7037-45ed-aa23-706f58358c0e)