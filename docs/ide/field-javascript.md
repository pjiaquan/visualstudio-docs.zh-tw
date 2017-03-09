---
title: "&lt;field&gt; (JavaScript) | Microsoft Docs"
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
  - "<field> JavaScript XML 標記"
  - "field JavaScript XML 標記"
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;field&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

針對物件所定義的欄位或成員指定文件資訊，包括描述。  
  
## 語法  
  
```  
<field name="fieldName" static="true|false"  
    type="FieldType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID"  
    value="code">description  
</field>  
```  
  
#### 參數  
 `name`  
 欄位或成員的名稱。  如果 `<field>` 項目用於建構函式時，則需要 `name` 並定義標記套用的成員。  當 `<field>` 項目直接標註的欄位時，這個屬性會被忽略，因此， Visual Studio 會使用名稱為實際欄位名稱原始程式碼。  
  
 `static`  
 選擇項。  指定欄位是否為建構函式的成員或建構函式所傳回之物件的成員。  設定至 `true` 以將欄位之集合做為建構函式的成員。  設定至 `false` 欄位之集合，物件的成員是由建構函式所傳回。  
  
 `type`  
 選擇項。  資料型別的欄位。  型別可以是下列其中一項：  
  
-   在 ECMAScript 5 規格的 ECMAScript 語言型別，例如 `Number` 和 `Object`。  
  
-   DOM 物件，例如 `HTMLElement`、 `Window`和 `Document`。  
  
-   JavaScript 建構函式。  
  
 `integer`  
 選擇項。  如果 `type` 是 `Number`，指定欄位是否為整數。  設定為 `true` 表示欄位是整數;否則會設為 `false`。  Visual Studio 不會使用這個屬性來提供 IntelliSense 資訊。  
  
 `domElement`  
 選擇項。  這個屬性已被取代；`type` 屬性會優先於這個屬性。  這個屬性指定文件的欄位是 DOM 項目。  設定為 `true` 指定欄位是 DOM 項目;否則會設為 `false`。  如果 `type` 屬性未設定，而且 `domElement` 設定為 `true`時， IntelliSense 會在執行陳述式完成時將文件的欄位做為 `HTMLElement` 。  
  
 `mayBeNull`  
 選擇項。  指定文件的欄位是否可以設定為 null。  設定為 `true` 表示欄位可以設定為 null;否則會設為 `false`。  預設值是 `false`。  Visual Studio 不會使用這個屬性來提供 IntelliSense 資訊。  
  
 `elementType`  
 選擇項。  如果`type` 屬性是 `Array`，則此屬性指定在陣列裡的元素型別。  
  
 `elementInteger`  
 選擇項。  如果 `type` 是 `Array` ，而且 `elementType` 是 `Number`，則這個屬性指定陣列中的項目是否為整數。  設定為 `true` 以表示陣列中的元素是整數；否則會設為 `false`。  Visual Studio 不會使用這個屬性來提供 IntelliSense 資訊。  
  
 `elementDomElement`  
 選擇項。  這個屬性已被取代；`elementType` 屬性會優先於這個屬性。  如果 `type` 是 `Array`，則這個屬性指定陣列中的項目是否為 DOM 項目。  設定為 `true` 指定項目是 DOM 項目；否則會設為 `false`。  如果 `elementType` 屬性尚未設定，且 `elementDomElement` 設定為 `true`時， IntelliSense 會在執行陳述式完成時將在陣列的每個元素做為 `HTMLElement` 。  
  
 `elementMayBeNull`  
 選擇項。  如果 `type` 是 `Array`，則指定陣列中的項目是否可以設定為 null。  設定為 `true` 以表示陣列中的項目可以設定為 null；否則會設為 `false`。  預設值是 `false`。  Visual Studio 不會使用這個屬性來提供 IntelliSense 資訊。  
  
 `helpKeyword`  
 選擇項。  F1 Help 的關鍵字。  
  
 `locid`  
 選擇項。  識別項對欄位的當地語系化資訊。  識別項是成員 ID，或其對應於 OpenAjax 中繼資料在訊息繫結所定義的 `name` 屬性值。  識別項的型別取決於在 [\<loc\>](../ide/loc-javascript.md) 標記中指定的格式。  
  
 `value`  
 選擇項。  指定程式碼，而此程式碼應該由IntelliSense評估而不是由函式程式碼本身評估使用。  對於 `<field>`，這個屬性為建構函式支援，不過沒有物件文字支援。  表示欄位型別未定義時，您可以使用這個屬性會提供型別資訊。  例如，您可以使用 `value=’1’` 將欄位型別為數字。  
  
 `description`  
 選擇項。  欄位的描述。  
  
## 備註  
 當您記錄建構函式的欄位時，`name` 屬性是被要求的。  針對其他案例， `<field>` 項目的所有屬性都是選擇性的。  
  
 當您記錄建構函式時， `<field>` 項目必須在欄位宣告之前。  `name` 屬性必須符合原始程式碼中使用的欄位名稱。  如需物件成員， `<field>` 項目，則在物件成員宣告之前，發生於 `name` 屬性可以省略。  
  
## 範例  
 下列程式碼範例顯示如何使用 `<field>` 元素。  
  
```javascript  
// Use of <field> in an object definition.  
var Rectangle = {  
    /// <field type='Number'>The width of the rectangle.</field>  
    wid: 5,  
    /// <field type='Number'>The length of the rectangle.</field>  
    len: 0,  
    /// <field type='Number'>Returns the area of the rectangle.</field>  
    getArea: function (wid, len) {  
        return len * wid;  
    }  
}  
  
// Use of <field> in a constructor function.  
// The name attribute is required.  
function Engine() {  
    /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
    this.HorsePower = 150;  
}  
```  
  
## 範例  
 下列範例顯示如何使用 `static` 屬性的`<field>`元素設定 `true`。  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
// IntelliSense on the field is available here.  
Engine.  
  
```  
  
## 範例  
 下列範例顯示如何使用 `static` 屬性的`<field>`元素設定 `false`。  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='false' type='Number'>Non-static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
var eng = new Engine();  
// IntelliSense on the field is available here.  
eng.  
  
```  
  
## 範例  
 下列範例示範如何對 `value` 屬性使用 `<field>` 項目。  
  
```javascript  
function calculator(a) {  
    /// <field name='f' value='1'/>  
}  
new calculator().f.   // Completion list for a Number.  
  
```  
  
## 請參閱  
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)