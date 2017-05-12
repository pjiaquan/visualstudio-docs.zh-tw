---
title: "global 屬性 (規則運算式) (JavaScript) | Microsoft Docs"
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
  - "Global"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "global 屬性"
ms.assetid: 76a0f115-0d89-4aca-86d5-932895c6d649
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# global 屬性 (規則運算式) (JavaScript)
傳回布林值，這個值表示搭配規則運算式使用之全域旗標 \(**g**\) 的狀態。  預設值為 **false**。  唯讀。  
  
## 語法  
  
```  
  
rgExp.global  
```  
  
## 備註  
 必要的 `rgExp` 參考是**規則運算式**物件的執行個體。  
  
 如果已針對規則運算式設定全域旗標，`global` 屬性會傳回 **true**，否則會傳回 **false**。  
  
 若使用全域旗標，則表示搜尋功能應該在搜尋字串中找出所有出現此模式的地方，而不只是找出第一次出現的地方。  這也稱為全域比對。  
  
## 範例  
 下列範例說明 `global` 屬性的使用方式。  如果您將 **g** 傳入底下顯示的函式，則會將所有的單字 "the" 全部取代成 "a"。  請注意，因為您並未將 **i** \(忽略大小寫\) 旗標傳遞至該函式，所以不會取代字串開頭的 "The"。  
  
 這個函式會顯示與可允許的規則運算式旗標 \(**g**、**i** 和 **m**\) 相關聯的屬性條件。  此函式也會顯示已完成所有取代的字串。  
  
```javascript  
function RegExpPropDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The batter hit the ball with the bat ";  
   ss += "and the fielder caught the ball with the glove.";  
  
   //Replace "the" with "a".  
   var re = new RegExp("the", flag);  
   var r = ss.replace(re, "a");          
  
   // Output the resulting string and the flags.  
   var s = "";  
   s += "global: " + re.global.toString();  
   s += "<br />";  
   s += "ignoreCase: " + re.ignoreCase.toString();  
   s += "<br />";  
   s += "multiline: " + re.multiline.toString();  
   s += "<br />";  
   s += "Resulting String: " + r;  
  
   return (s);  
}  
  
document.write(RegExpPropDemo("g"));  
```  
  
## 範例  
 下列是產生的輸出。  
  
```javascript  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用於**：[規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)  
  
## 請參閱  
 [ignoreCase 屬性 \(規則運算式\)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [multiline 屬性 \(規則運算式\)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-tw/ab0766e1-7037-45ed-aa23-706f58358c0e)