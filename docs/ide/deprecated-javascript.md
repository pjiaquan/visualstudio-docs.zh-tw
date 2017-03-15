---
title: "&lt;deprecated&gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;deprecated&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定已取代的函式或方法。  
  
## 語法  
  
```  
<deprecated  
    type="deprecate|remove"  
    locid="descriptionID">description  
</deprecated>  
```  
  
#### 參數  
 `type`  
 選擇項。  指定函式或方法是否已在未來的發行版本中移除，或是否已經移除函式或方法，其使用可能會造成錯誤。  設定為 `deprecate` 指定函式或方法在未來的發行版本中移除。  設定為 `remove` 指定已經移除函式或方法。  
  
 `locid`  
 選擇項。  函式或方法的當地語系化資訊識別項。  識別項是成員 ID 或其對應於 OpenAjax 中繼資料在訊息繫結所定義的 `name` 屬性值。  識別項的型別取決於在 [\<loc\>](../ide/loc-javascript.md) 項目中指定的格式。  
  
 `description`  
 選擇項。  已遭取代函式或方法的說明。  
  
## 備註  
 用以註解函式的元素，包含`<deprecated>`，必須將其置放在函式主體中任何陳述式之前。  當您將一個函式取代成時，建議您以 `<deprecated>` 項目取代的 [\<summary\>](../ide/summary-javascript.md) 項目。  
  
## 範例  
 下列程式碼將示範如何使用 `<deprecated>` 項目。  
  
```javascript  
function areaFunction(radiusParam) {  
    /// <deprecated type="deprecate" >Determines the area of a circle when supplied a radius parameter.</deprecated>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## 請參閱  
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)