---
title: "&lt;summary&gt; (JavaScript) | Microsoft Docs"
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
  - "summary JavaScript XML 標記"
  - "<summary> JavaScript XML 標記"
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;summary&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

針對函式或方法指定描述。  
  
## 語法  
  
```  
<summary locid="descriptionID">description  
</summary>  
```  
  
#### 參數  
 `locid`  
 選擇項。  函式或方法的當地語系化資訊識別項。  識別項是成員 ID，或其對應於 OpenAjax 中繼資料在訊息繫結所定義的 `name` 屬性值。  識別項的型別取決於在 [\<loc\>](../ide/loc-javascript.md) 項目中指定的格式。  
  
 `description`  
 選擇項。  函式或方法的說明。  
  
## 備註  
 在任何陳述式之前的函式主體，必須用於加註函式的項目，包括 [\<summary\>](../ide/summary-javascript.md)、 [\<param\>](../ide/param-javascript.md)和 [\<returns\>](../ide/returns-javascript.md)，。  
  
## 範例  
 下列程式碼將示範如何使用 `<summary>` 項目。  
  
```javascript  
function areaFunction(radiusParam)  
{  
    /// <summary>Determines the area of a circle when supplied a radius parameter.</summary>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## 請參閱  
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)