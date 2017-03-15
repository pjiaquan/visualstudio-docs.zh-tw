---
title: "&lt;var&gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<var> JavaScript XML 標記"
  - "var JavaScript XML 標記"
ms.assetid: 34ff9023-c81c-46d1-85b6-0022f0962e66
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;var&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

為變數指定文件資訊。  
  
## 語法  
  
```  
<var type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID">description  
</var>  
  
```  
  
#### 參數  
 `type`  
 選擇項。  變數的資料型別。   型別可以是下列其中一項:  
  
-   在 ECMAScript 5 規格，例如 `Number` 和 `Object`的 ECMAScript 語言型別。  
  
-   DOM 物件，例如 `HTMLElement`、 `Window`和 `Document`。  
  
-   JavaScript 建構函式。  
  
 `integer`  
 選擇項。  如果 `type` 是 `Number`，指定變數是否為整數。  設定為 `true` 表示變數是整數;否則會設為 `false`。  Visual Studio 不會使用這個屬性提供 IntelliSense 資訊。  
  
 `domElement`  
 選擇項。  這個屬性已被取代; `type` 屬性會優先於這個屬性。  這個屬性指定文件的變數是 DOM 項目。  設定為 `true` 指定變數是 DOM 項目;否則會設為 `false`。  如果 `type` 屬性未設定，而且 `domElement` 設定為 `true`時， IntelliSense 會在執行陳述式完成時將文件的變數做為 `HTMLElement` 。  
  
 `mayBeNull`  
 選擇項。  指定文件的變數是否可以設定為 null。  設定為 `true` 表示變數可以設定為 null;否則會設為 `false`。  預設值是 `false`。  Visual Studio 不會使用這個屬性提供 IntelliSense 資訊。  
  
 `elementType`  
 選擇項。  如果`type` 屬性是 `Array`，此屬性指定在陣列裡的元素型別。  
  
 `elementInteger`  
 選擇項。  如果 `type` 是 `Array` ，而且 `elementType` 是 `Number`，則這個屬性指定陣列中的項目是否為整數。  設定為 `true` 表示陣列中的元素是整數;否則會設為 `false`。  Visual Studio 不會使用這個屬性提供 IntelliSense 資訊。  
  
 `elementDomElement`  
 選擇項。  這個屬性已被取代; `elementType` 屬性會優先於這個屬性。  如果 `type` 是 `Array`，則這個屬性指定陣列中的項目是否為 DOM 項目。  設定為 `true` 指定項目是 DOM 項目;否則會設為 `false`。  如果 `elementType` 屬性未設定，而且 `elementDomElement` 設定為 `true`時， IntelliSense 會在執行陳述式完成時將在陣列的每個元素做為 `HTMLElement` 。  
  
 `elementMayBeNull`  
 選擇項。  如果 `type` 是 `Array`，指定陣列中的項目是否可以設定為 null。  設定為 `true` 表示陣列中的項目可以設定為 null;否則會設為 `false`。  預設值是 `false`。  Visual Studio 不會使用這個屬性提供 IntelliSense 資訊。  
  
 `helpKeyword`  
 選擇項。  F1 Help 的關鍵字。  
  
 `locid`  
 選擇項。  識別項對變數的當地語系化資訊。  在訊息繫結的 `name` 屬性值所定義識別項是或成員 ID 或其對應於 OpenAjax 中繼資料。  識別項的型別取決於在 [\<loc\>](../ide/loc-javascript.md) 標記中指定的格式。  
  
 `description`  
 選擇項。  變數的描述。  
  
## 範例  
 下列程式碼範例顯示如何使用 `<var>` 元素。  
  
```javascript  
/// <var>A rectangle that has a width of 5.</var>  
var Rectangle = {  
    /// <field type = 'Number'>The width of the rectangle.</field>  
    wid: 5,  
    /// <field type = 'Number'>The length of the rectangle.</field>  
    len: 0,  
    /// <field type='Number'>Returns the area of the rectangle.</field>  
    getArea: function (wid, len) {  
        return len * wid;  
    }  
}  
```  
  
## 請參閱  
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)