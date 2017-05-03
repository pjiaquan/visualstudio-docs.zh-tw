---
title: "hasOwnProperty 方法 (Object) (JavaScript) | Microsoft Docs"
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
  - "hasOwnProperty"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "hasOwnProperty 方法"
ms.assetid: 3eb69d69-486f-4792-9518-4452aef369ca
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# hasOwnProperty 方法 (Object) (JavaScript)
判斷物件是否有指定之名稱的屬性。  
  
## 語法  
  
```  
  
object.hasOwnProperty(proName)  
```  
  
## 參數  
 `object`  
 必要項。  物件的執行個體。  
  
 `proName`  
 必要項。  屬性名稱的字串值。  
  
## 備註  
 如果 `object` 有指定之名稱的屬性，`hasOwnProperty` 方法會傳回 `true`，否則會傳回 `false`。  這個方法不會檢查物件原型鏈結中有哪些屬性，因此您指定的屬性必須是物件本身的成員。  
  
 Internet Explorer 8 或以下版本的主物件不支援這個屬性。  
  
## 範例  
 在以下範例中，所有 `String` 物件共用一個 split 方法。  下列程式碼會顯示 **false** 和 **true**。  
  
```javascript  
var s = new String("Sample");  
document.write(s.hasOwnProperty("split"));  
document.write("<br/>");  
document.write(String.prototype.hasOwnProperty("split"));  
  
// Output:  
// false  
// true  
  
```  
  
## 需求  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 請參閱  
 [in 運算子](../../javascript/reference/in-operator-decrementjavascript.md)