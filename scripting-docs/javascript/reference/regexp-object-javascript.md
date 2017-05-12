---
title: "RegExp 物件 (JavaScript) | Microsoft Docs"
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
  - "RegExp"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "RegExp 物件"
  - "RegExp 物件, 概觀"
ms.assetid: 7f6b1073-8cbb-49ed-94b6-56833ba663c5
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# RegExp 物件 (JavaScript)
用來儲存有關規則運算式模式比對結果之相關資訊的內建全域物件。  
  
## 語法  
  
```  
  
RegExp.property   
```  
  
## 備註  
 必要的 *property* 引數可以是任何一個 `RegExp` 物件屬性。  
  
 `RegExp` 物件不能直接建立，但是隨時都可以使用。  在成功完成規則運算式搜尋之前，`RegExp` 物件的各種屬性初始值如下：  
  
|屬性|速記|初始值|  
|--------|--------|---------|  
|index||\-1|  
|input|$\_|空字串。|  
|lastIndex||\-1|  
|lastMatch|$&|空字串。|  
|lastParen|$\+|空字串。|  
|leftContext|$\`|空字串。|  
|rightContext|$'|空字串。|  
|$1 \- $9|$1 \- $9|空字串。|  
  
 在成功完成規則運算式搜尋之前，其屬性都有未定義的值。  
  
 請不要混淆全域 `RegExp` 物件與**規則運算式**物件。  即使兩者看起來像是同一件事，但實際上並不相同。  全域 `RegExp` 物件的屬性包含每次比對發生時持續更新的相關資訊，而**規則運算式**物件的屬性只包含該**規則運算式**執行個體比對時的相關資訊。  
  
## 範例  
 下列範例會執行規則運算式搜尋。  它會顯示全域 `RegExp` 物件中及 `exec` 方法所傳回之陣列中的相符項目與子相符項目。  
  
```javascript  
var newLine = "<br />";  
  
var re = /(\w+)@(\w+)\.(\w+)/g  
var src = "Please send mail to george@contoso.com and someone@example.com. Thanks!"  
  
var result;  
var s = "";  
  
// Get the first match.  
result = re.exec(src);  
  
while (result != null) {  
    // Show the entire match.  
    s += newLine;  
  
    // Show the match and submatches from the RegExp global object.  
    s += "RegExp.lastMatch: " + RegExp.lastMatch + newLine;  
    s += "RegExp.$1: " + RegExp.$1 + newLine;  
    s += "RegExp.$2: " + RegExp.$2 + newLine;  
    s += "RegExp.$3: " + RegExp.$3 + newLine;  
  
    // Show the match and submatches from the array that is returned  
    // by the exec method.  
    for (var index = 0; index < result.length; index++) {  
        s +=  index + ": ";  
        s += result[index];  
        s += newLine;  
    }  
  
    // Get the next match.  
    result = re.exec(src);  
}  
document.write(s);  
  
// Output:  
//  RegExp.lastMatch: george@contoso.com  
//  RegExp.$1: george  
//  RegExp.$2: contoso  
//  RegExp.$3: com  
//  0: george@contoso.com  
//  1: george  
//  2: contoso  
//  3: com  
  
//  RegExp.lastMatch: someone@example.com  
//  RegExp.$1: someone  
//  RegExp.$2: example  
//  RegExp.$3: com  
//  0: someone@example.com  
//  1: someone  
//  2: example  
//  3: com  
  
```  
  
<a name="js56jsobjregexpprop"></a>   
## 屬性  
 [$1...$9 屬性](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md) &#124; [index 屬性](../../javascript/reference/index-property-regexp-javascript.md) &#124; [input 屬性](../../javascript/reference/input-property-dollar-regexp-javascript.md) &#124; [lastIndex 屬性](../../javascript/reference/lastindex-property-regexp-javascript.md) &#124; [lastMatch 屬性](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md) &#124; [lastParen 屬性](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md) &#124; [leftContext 屬性](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md) &#124; [rightContext 屬性](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)  
  
## 方法  
 `RegExp` 物件沒有方法。  
  
## 需求  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 請參閱  
 [規則運算式物件](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/zh-tw/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String 物件](../../javascript/reference/string-object-javascript.md)