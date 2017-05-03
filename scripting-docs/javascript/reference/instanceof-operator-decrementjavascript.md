---
title: "instanceof 運算子 (JavaScript) | Microsoft Docs"
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
  - "instanceof_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "instanceOf 運算子"
ms.assetid: 92467bdc-56b5-42dc-adbd-a219776454d2
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# instanceof 運算子 (JavaScript)
傳回的布林值將說明物件是否為某個特定類別的執行個體。  
  
## 語法  
  
```  
  
result = object instanceof class  
```  
  
## 參數  
 `result`  
 必要項。  任何變數。  
  
 `object`  
 必要項。  任何物件運算式。  
  
 `class`  
 必要項。  任何定義的物件類別。  
  
## 備註  
 如果 `object` 是 `class` 的執行個體，`instanceof` 運算子會傳回 `true`。  如果 `class` 存在於物件的原型鏈結中，則傳回 `true` \(如果為 `true`\)。  如果 `object` 不是 `class` 的執行個體，或者如果 `object` 為 `null`，則會傳回 `false`。  
  
## 範例  
 下面範例會示範如何使用 `instanceof` 運算子。  
  
```javascript  
function objTest(obj){  
    var i, t, s = "";  
    t = new Array();  
    t["Date"] = Date;  
    t["Object"] = Object;  
    t["Array"] = Array;  
        for (i in t){  
            if (obj instanceof t[i]) {   
                s += "obj is an instance of " + i + "<br/>";  
            }  
            else {  
                s += "obj is not an instance of " + i + "<br/>";  
        }  
    }  
    return(s);  
}  
  
var obj = new Date();  
document.write(objTest(obj));  
  
// Output:   
// obj is an instance of Date  
// obj is an instance of Object  
// obj is not an instance of Array  
```  
  
## 需求  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## 請參閱  
 [運算子優先順序](../../javascript/operator-subtractprecedence-javascript.md)   
 [運算子摘要 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)