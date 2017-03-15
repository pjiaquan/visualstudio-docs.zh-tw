---
title: "&lt;returns&gt; (JavaScript) | Microsoft Docs"
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
  - "傳回 JavaScript XML 標記"
  - "<returns> JavaScript XML 標記"
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;returns&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定文件資訊，其文件資訊是關於函式結果或方法呼叫的結果。  
  
## 語法  
  
```  
<returns type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID" value="code">description  
</returns>  
```  
  
#### 參數  
 `type`  
 選擇項。  傳回值的資料類型。  型別可以是下列其中一項：  
  
-   在 ECMAScript 5 規格的 ECMAScript 語言型別，例如 `Number` 和 `Object`。  
  
-   DOM 物件，例如 `HTMLElement`、 `Window`和 `Document`。  
  
-   JavaScript 建構函式。  
  
 `integer`  
 選擇項。  如果 `type` 是 `Number`，則指定傳回值是否為整數。  設定為 `true` 以表示傳回值為整數；否則會設為 `false`。  Visual Studio 不會使用這個屬性來提供 IntelliSense 資訊。  
  
 `domElement`  
 選擇項。  這個屬性已被取代；`type` 屬性會優先於這個屬性。  這個屬性指定文件的傳回值是 DOM 項目。  設定為 `true` 指定傳回數是 DOM 項目；否則會設為 `false`。  如果 `type` 屬性尚未設定，而且 `domElement` 設定為 `true`時， IntelliSense 會在執行陳述式完成時將文件的傳回數做為 `HTMLElement` 。  
  
 `mayBeNull`  
 選擇項。  指定文件的傳回值是否可以設定為 null。  設定為 `true` 來表示傳回數可以設定為 null；否則會設為 `false`。  預設值是 `false`。  Visual Studio 不會使用這個屬性來提供 IntelliSense 資訊。  
  
 `elementType`  
 選擇項。  如果`type` 屬性是 `Array`，則此屬性指定在陣列裡的元素型別。  
  
 `elementInteger`  
 選擇項。  如果 `type` 是 `Array` ，而且 `elementType` 是 `Number`，則這個屬性指定陣列中的項目是否為整數。  設定為 `true` 以表示陣列中的元素是整數；否則會設為 `false`。  Visual Studio 不會使用這個屬性來提供 IntelliSense 資訊。  
  
 `elementDomElement`  
 選擇項。  這個屬性已被取代；`elementType` 屬性會優先於這個屬性。  如果 `type` 是 `Array`，則這個屬性指定陣列中的項目是否為 DOM 項目。  設定為 `true` 指定項目是 DOM 項目；否則會設為 `false`。  如果 `elementType` 屬性尚未設定，且 `elementDomElement` 設定為 `true`時， IntelliSense 會在執行陳述式完成時將在陣列的每個元素做為 `HTMLElement` 。  
  
 `elementMayBeNull`  
 選擇項。  如果 `type` 是 `Array`，則指定陣列中的項目是否可以設定為 null。  設定為 `true` 以表示陣列中的項目可以設定為 null；否則會設為 `false`。  預設值是 `false`。  Visual Studio 不會使用這個屬性來提供 IntelliSense 資訊。  
  
 `locid`  
 選擇項。  關於傳回值的當地語系化資訊之識別項。  識別項是成員 ID，或其對應於 OpenAjax 中繼資料在訊息繫結所定義的 `name` 屬性值。  識別項的型別取決於在 [\<loc\>](../ide/loc-javascript.md) 標記中指定的格式。  
  
 `value`  
 選擇項。  指定程式碼，而此程式碼應該由IntelliSense評估而不是由函式程式碼本身評估使用。  舉例來說，您可以使用這個屬性為非同步回呼，例如 `Promise`，來提供 IntelliSense。  與 `<returns>` 項目使用 `value` 屬性可以略過冗長的程式碼執行來增進IntelliSense 效能。  
  
 `description`  
 選擇項。  為傳回值的描述。  
  
## 備註  
 `<returns>` 項目必須置於任何陳述式之前的函式主體。  
  
## 範例  
 下列程式碼範例顯示如何使用 `<returns>` 元素。  
  
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
  
// The following examples use the <remarks> element with a value attribute.  
  
function getJson(complete) {   
    /// <returns value='complete("")' ></returns>  
    var r = new XMLHttpRequest();   
    // . . .   
}   
  
getJson(function (json) {   
    json.  // IntelliSense for a String object is   
           // available here.  
});  
  
function calculate(x) {  
    /// <returns value='1'/>  
}  
calculate().  // Completion list for a Number.  
  
```  
  
## 請參閱  
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)