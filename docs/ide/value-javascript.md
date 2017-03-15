---
title: "&lt;value&gt; (JavaScript) | Microsoft Docs"
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
  - "<value> JavaScript XML 標記"
  - "value JavaScript XML 標記"
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;value&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

為 `get` 及 `set` 函式的 ECMAScript 3 屬性指定文件資訊。  
  
## 語法  
  
```  
<value type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID">description  
</value>  
```  
  
#### 參數  
 `type`  
 選擇項。  屬性的資料型別。  型別可以是下列其中一項：  
  
-   在 ECMAScript 5 規範中 ECMAScript 的語言型別，例如 `Number` 和 `Object`。  
  
-   DOM 物件，例如 `HTMLElement`、 `Window`和 `Document`。  
  
-   JavaScript 建構函式。  
  
 `integer`  
 選擇項。  如果 `type` 是 `Number`，則指定其屬性是否為整數。  設定為 `true` 表示其屬性為整數；否則會設為 `false`。  Visual Studio 不會使用這個屬性來提供 IntelliSense 資訊。  
  
 `domElement`  
 選擇項。  這個屬性已被取代；`type` 屬性會優先於這個屬性。  這個屬性指定文件的屬性是否為 DOM 項目。  設定為 `true` 指定其屬性為 DOM 項目；否則會設為 `false`。  如果 `type` 屬性未設定，而且 `domElement` 設定為 `true`時， IntelliSense 會在執行陳述式完成時將文件的屬性做為 `HTMLElement` 。  
  
 `mayBeNull`  
 選擇項。  指定文件的屬性是否可以設定為 null。  設定為 `true` 表示其屬性可以設定為 null；否則會設為 `false`。  預設值是 `false`。  Visual Studio 不會使用這個屬性來提供 IntelliSense 資訊。  
  
 `elementType`  
 選擇項。  如果`type` 屬性是 `Array`，則此屬性指定在陣列裡的元素型別。  
  
 `elementInteger`  
 選擇項。  如果 `type` 是 `Array` ，而且 `elementType` 是 `Number`，則這個屬性指定陣列中的項目是否為整數。  設定為 `true` 表示陣列中的元素是整數；否則會設為 `false`。  Visual Studio 不會使用這個屬性來提供 IntelliSense 資訊。  
  
 `elementDomElement`  
 選擇項。  這個屬性已被取代；`elementType` 屬性會優先於這個屬性。  如果 `type` 是 `Array`，則這個屬性指定陣列中的項目是否為 DOM 項目。  設定為 `true` 指定項目為 DOM 項目；否則設為 `false`。  如果 `elementType` 屬性尚未設定，且 `elementDomElement` 設定為 `true`時， IntelliSense 會在執行陳述式完成時將在陣列的每個元素做為 `HTMLElement` 。  
  
 `elementMayBeNull`  
 選擇項。  如果 `type` 是 `Array`，則指定陣列中的項目是否可以設定為 null。  設定為 `true` 以表示陣列中的項目可以設定為 null；否則設為 `false`。  預設值是 `false`。  Visual Studio 不會使用這個屬性來提供 IntelliSense 資訊。  
  
 `locid`  
 選擇項。  對屬性的當地語系化資訊之識別項。  識別項是成員 ID 或其對應於 OpenAjax 中繼資料在訊息繫結所定義的 `name` 屬性值。  識別項的型別取決於在 [\<loc\>](../ide/loc-javascript.md) 項目中指定的格式。  
  
 `description`  
 選擇項。  屬性的描述。  
  
## 備註  
 ECMAScript 5 屬性使用 [\<summary\>](../ide/summary-javascript.md) 項目。  
  
 在使用 `get` 或 `set` 函式前，使用 `<value>` 項目。  
  
## 範例  
 下列程式碼範例示範如何使用 `get` 函式上的 `<value>` 項目。  
  
```javascript  
function Sys$CancelEventArgs$get_cancel() {  
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>  
    if (arguments.length !== 0) throw Error.parameterCount();  
    return this._cancel();  
}  
```  
  
## 請參閱  
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)