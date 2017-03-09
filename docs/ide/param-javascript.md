---
title: "&lt;param&gt; (JavaScript) | Microsoft Docs"
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
  - "<param> JavaScript XML 標記"
  - "param JavaScript XML 標記"
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;param&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在函式或方法為參數指定文件資訊。  
  
## 語法  
  
```  
<param name="parameterName" type="ParameterType"  
    integer="true|false" domElement="true|false"  
    mayBeNull="true|false" elementType="ArrayElementType"  
    elementInteger="true|false" elementDomElement="true|false"  
    elementMayBeNull="true|false" locid="descriptionID"  
    parameterArray="true|false" optional="true|false"  
    value="code">description  
</param>  
```  
  
#### 參數  
 `name`  
 必要項。  參數名稱。  
  
 `type`  
 選擇項。  參數的資料型別。  型別可以是下列其中一項：  
  
-   在 ECMAScript 5 規格的 ECMAScript 語言型別，例如 `Number` 和 `Object`。  
  
-   DOM 物件，例如 `HTMLElement`、 `Window`和 `Document`。  
  
-   JavaScript 建構函式。  
  
 `integer`  
 選擇項。  如果 `type` 是 `Number`，指定參數是否為整數。  設定為 `true` 表示參數是整數；否則會設為 `false`。  Visual Studio 不會使用這個屬性來提供 IntelliSense 資訊。  
  
 `domElement`  
 選擇項。  這個屬性已被取代；`type` 屬性會優先於這個屬性。  這個屬性指定文件的參數是 DOM 項目。  設定為 `true` 指定參數是 DOM 項目；否則會設為 `false`。  如果 `type` 屬性未設定，而且 `domElement` 設定為 `true`時， IntelliSense 會在執行陳述式完成時將文件的參數做為 `HTMLElement` 。  
  
 `mayBeNull`  
 選擇項。  指定文件的參數是否可以設定為 null。  設定為 `true` 表示參數可以設定為 null；否則會設為 `false`。  預設值是 `false`。  Visual Studio 不會使用這個屬性來提供 IntelliSense 資訊。  
  
 `elementType`  
 選擇項。  如果`type` 屬性是 `Array`，則此屬性指定在陣列裡的元素型別。  
  
 `elementInteger`  
 選擇項。  如果 `type` 是 `Array` ，而且 `elementType` 是 `Number`，則這個屬性指定陣列中的項目是否為整數。  設定為 `true` 以表示陣列中的元素是整數；否則會設為 `false`。  Visual Studio 不會使用這個屬性來提供 IntelliSense 資訊。  
  
 `elementDomElement`  
 選擇項。  這個屬性已被取代；`elementType` 屬性會優先於這個屬性。  如果 `type` 是 `Array`，則這個屬性指定陣列中的項目是否為 DOM 項目。  設定為 `true` 指定項目是 DOM 項目；否則會設為 `false`。  如果 `elementType` 屬性尚未設定，且 `elementDomElement` 設定為 `true`時， IntelliSense 會在執行陳述式完成時將在陣列的每個元素做為 `HTMLElement` 。  
  
 `elementMayBeNull`  
 選擇項。  如果 `type` 是 `Array`，則指定陣列中的項目是否可以設定為 null。  設定為 `true` 以表示陣列中的項目可以設定為 null；否則會設為 `false`。  預設值是 `false`。  Visual Studio 不會使用這個屬性來提供 IntelliSense 資訊。  
  
 `locid`  
 選擇項。  識別項對參數數的當地語系化資訊。  識別項是成員 ID 或其對應於 OpenAjax 中繼資料在訊息繫結所定義的 `name` 屬性值。  識別項的型別取決於在 [\<loc\>](../ide/loc-javascript.md) 項目中指定的格式。  
  
 `parameterArray`  
 選擇項。  指定文件的參數是否可以在函式呼叫重複，類似於迴圈在 `String.format` 函式支援的參數。  設定為 `true` 表示參數可以重複；否則會設為 `false`。  Visual Studio 不會使用這個屬性來提供 IntelliSense 資訊。  
  
 `optional`  
 選擇項。  指定文件的參數是否為在呼叫的函式的選擇性項目。  設定為 `true` 表示參數是選擇性項目；否則會設為 `false`。  
  
 `value`  
 選擇項。  指定程式碼，而此程式碼應該由 IntelliSense 評估而不是由函式程式碼本身評估使用。  當參數型別未定義時，您可以使用這個屬性提供型別資訊。  例如，您可以使用 `value=’1’` 將參數型別做為數字。  
  
 `description`  
 選擇項。  參數的描述。  
  
## 備註  
 必要屬性只有 `name`。  所有其他屬性都是選擇性的。  
  
 在任何陳述式之前的函式主體，必須用於加註函式的項目，例如 [\<summary\>](../ide/summary-javascript.md)、 [\<param\>](../ide/param-javascript.md)和 [\<returns\>](../ide/returns-javascript.md)，。  
  
 如果有相同名稱的多個 `<param>` 項目，請使用其中一個 `<param>` 項目，還可以會忽略多餘的項目。  判斷哪個項目使用未定義的行為。  如果 `name` 參考不存在的參數，則會忽略項目。  
  
## 範例  
 下列程式碼範例顯示如何使用 `<param>` 元素。  
  
```javascript  
function areaFunction(radiusParam)  
{  
    /// <summary>Determines the area of a circle when provided a radius parameter.</summary>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
// Uses of <param> with the value attribute.  
  
function calculate(a) {  
    /// <param name='a' value='1'/>  
    a.    // Completion list for a Number.  
}  
  
function calculate(a) {  
    /// <param name='a' value='{x:0,y:0}'/>  
    a.    // x and y appear in the completion list.  
}  
  
```  
  
## 請參閱  
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)